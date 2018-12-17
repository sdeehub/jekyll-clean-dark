---
layout: post
title: "การใช้ PhpSpreadsheet ร่วมกับ Yii2 (บันทึกความจำ 1/3)"
date: 2018-12-14 11:41:55 +0700
description: ตัวอย่างงานที่เอา PhpSpreadsheet มาใช้กับ Yii2 Framework เพื่ออ่านและเขียนไฟล์ Excel
tags:
  - Yii2
comments: true
---
ลักษณะโจทย์งาน: เขียนงานด้วย PHP โดยใช้ Yii2 Framework - มีการทำฐานข้อมูลให้มี UI ที่หน้าจอ บวกกับอ่านข้อมูลที่เป็นไฟล์ Excel จัดการข้อมูลทำผลลัพธ์ออก UI ที่หน้าจอ และทำผลลัพธ์ออกมาเป็นไฟล์ Excel ด้วย

ข้อมูลอ้างอิงของ PhpSpreadsheet: [PhpSpreadsheet's documentation](https://phpspreadsheet.readthedocs.io/en/develop/)

เริ่มต้นใช้งาน PhpSpreadsheet: `composer.json`
```
"require": {
    "php": ">=5.4.0",
    "yiisoft/yii2": "~2.0.14",
    "yiisoft/yii2-bootstrap": "~2.0.0",
    "yiisoft/yii2-swiftmailer": "~2.0.0",
    "dmstr/yii2-adminlte-asset": "^2.1",
    "wbraganca/yii2-dynamicform": "*",
    "kartik-v/yii2-grid": "@dev",
    "kartik-v/yii2-tabs-x": "*",
    "kartik-v/yii2-datecontrol": "@dev",
    "kartik-v/yii2-widget-datepicker": "@dev",
    "kartik-v/yii2-widget-datetimepicker": "*",
    "phpoffice/phpspreadsheet": "^1.2"
  }
```

Controller: Function ที่อ่านไฟล์ Excel
```php
/**
 * Creates a new Rfq model.
 * If creation is successful, the browser will be redirected to the 'view' page.
 * @return mixed
 */
public function actionCreateExcelUpload()
{
    $modelRfqTrackingDummy = new RfqTrackingDummy();
    $model = new Rfq();

    if (Yii::$app->request->post())
    {
        $model->load(Yii::$app->request->post());

        $file_excel = UploadedFile::getInstance($model, 'get_excel');

        if (! empty($file_excel))
        {
            $model->rfq_excel_file = substr(md5(rand(1,1000).time()),0,15) . '.' . $file_excel->extension;
            $file_excel->saveAs('uploads/rfq_excel_file/' . $model->rfq_excel_file);

            $transaction = \Yii::$app->db->beginTransaction();
            try
            {
                $modelRfqTrackingDummy->save(false);
                $model->rfq_no = 'RFQ-' . $modelRfqTrackingDummy->id;

                // Validate all models
                $valid = $model->validate();

                if ($valid)
                {
                    $reader = new \PhpOffice\PhpSpreadsheet\Reader\Xlsx();
                    $spreadSheet = $reader->load("uploads/rfq_excel_file/" . $model->rfq_excel_file);

                    $sheet = $spreadSheet->getSheet(0);
                    $model->project = $sheet->getCell('F3')->getValue();
                    $model->rfq_submission_date = $sheet->getCell('F5')->getValue();
                    $model->quotation_due_date = $sheet->getCell('F6')->getValue();
                    $model->rfq_status_id = 1;
                    $model->save(false);

                    $dataArray = $sheet->rangeToArray('C7:Z47', NULL, TRUE, TRUE, FALSE);
                    $getParts = [];
                    if (! empty($dataArray))
                    {
                        for ($i=0; $i<24; $i++)
                        {
                            $j = 2;
                            $doArrayI = false;
                            while ($j <= 41)
                            {
                                if (! empty($dataArray[$j][$i]))
                                {
                                  $doArrayI = true;
                                }
                                $j++;
                            }

                            if (($doArrayI) && ($dataArray[0][$i] != 'Remark'))
                            {
                                $modelRfqSummary[$i] = new RfqSummary();
                                $modelRfqSummary[$i]->material_type = $dataArray[2][$i];
                                $modelRfqSummary[$i]->drawing_no = $dataArray[3][$i];
                                $modelRfqSummary[$i]->material_spec_1 = $dataArray[4][$i];
                                $modelRfqSummary[$i]->material_spec_2 = $dataArray[5][$i];
                                $modelRfqSummary[$i]->material_color = $dataArray[6][$i];
                                $modelRfqSummary[$i]->part_name = $dataArray[7][$i];
                                $modelRfqSummary[$i]->part_no = $dataArray[8][$i];
                                $modelRfqSummary[$i]->car_maker = $dataArray[9][$i];
                                $modelRfqSummary[$i]->car_model = $dataArray[10][$i];
                                $modelRfqSummary[$i]->car_series_type = $dataArray[11][$i];
                                $modelRfqSummary[$i]->application_for = $dataArray[12][$i];
                                $modelRfqSummary[$i]->series_4wd_2wd = $dataArray[13][$i];
                                $modelRfqSummary[$i]->fr_rr_type = $dataArray[14][$i];
                                $modelRfqSummary[$i]->rh_lh_side = $dataArray[15][$i];
                                $modelRfqSummary[$i]->end_user_customer = $dataArray[16][$i];
                                $modelRfqSummary[$i]->destination = $dataArray[17][$i];

                                $value = str_replace(",","",$dataArray[19][$i]);
                                $value = floatval($value);
                                $modelRfqSummary[$i]->monthly_used_volume_option_1 = $value;

                                $value = str_replace(",","",$dataArray[20][$i]);
                                $value = floatval($value);
                                $modelRfqSummary[$i]->monthly_used_volume_option_2 = $value;

                                $value = str_replace(",","",$dataArray[21][$i]);
                                $value = floatval($value);
                                $modelRfqSummary[$i]->monthly_used_volume_option_3 = $value;

                                $modelRfqSummary[$i]->used_qty_per_1_fg = $dataArray[22][$i];

                                $value = str_replace(",","",$dataArray[23][$i]);
                                $value = floatval($value);
                                $modelRfqSummary[$i]->vechal_volume_per_year = $value;

                                $modelRfqSummary[$i]->model_life = $dataArray[24][$i];
                                $modelRfqSummary[$i]->model_period = $dataArray[25][$i];
                                $modelRfqSummary[$i]->sop = $dataArray[26][$i];
                                $modelRfqSummary[$i]->similar_or_comparable_item = $dataArray[27][$i];
                                $modelRfqSummary[$i]->rfq_reference_no = $dataArray[28][$i];

                                $modelRfqSummary[$i]->delivery_condition_frequency = $dataArray[30][$i];
                                $modelRfqSummary[$i]->delivery_place_1 = $dataArray[31][$i];
                                $modelRfqSummary[$i]->delivery_place_2 = $dataArray[32][$i];
                                $modelRfqSummary[$i]->incor_team = $dataArray[33][$i];
                                $modelRfqSummary[$i]->boi_export_for_fg = $dataArray[34][$i];
                                $modelRfqSummary[$i]->non_boi_domestic_sale = $dataArray[35][$i];
                                $modelRfqSummary[$i]->boi_ckd_ratio = $dataArray[36][$i];
                                $modelRfqSummary[$i]->hmt_material_use = $dataArray[37][$i];
                                $modelRfqSummary[$i]->separate_tooling_price = $dataArray[38][$i];
                                $modelRfqSummary[$i]->amortize_tooling_price = $dataArray[39][$i];
                                $modelRfqSummary[$i]->tooling_owner = $dataArray[40][$i];

                                $modelRfqSummary[$i]->rfq_status_id = 1;
                                $modelRfqSummary[$i]->rfq_no = $model->rfq_no;
                                $getParts[] = $i;
                            }
                        }
                    }
                    $modelRfqTracking = new RfqTracking();
                    $modelRfqTracking->save(false);

                    $model->rfq_no = 'RFQ-' . $modelRfqTracking->id;
                    $model->save(false);

                    foreach ($getParts as $getPart)
                    {
                        $modelRfqSummary[$getPart]->rfq_no = $model->rfq_no;
                        $modelRfqSummary[$getPart]->save(false);

                        $modelRfqUploadedFiles = new RfqUploadedFiles();
                        $modelRfqUploadedFiles->rfq_summary_id = $modelRfqSummary[$getPart]->id;
                        $modelRfqUploadedFiles->save(false);
                    }

                    $modelRfqLog = new RfqLog();

                    $modelRfqLog->rfq_no = $model->rfq_no;
                    $modelRfqLog->status = 1;
                    $modelRfqLog->action = 10; // Created by Excel
                    $modelRfqLog->remark = 'Creating a New RFQ (Excel)';
                    $modelRfqLog->save(false);

                    $modelRfqRemark = new RfqRemark();
                    $modelRfqRemark->rfq_no = $model->rfq_no;
                    $modelRfqRemark->save(false);

                    $transaction->commit();
                    return $this->redirect(['edit', 'id' => $model->id]);
                } else {
                    $transaction->rollBack();
                }
            } catch (Exception $e) {
                  $transaction->rollBack();
            }
        }
    }

    return $this->render('create_excel_upload', [
        'model' => $model,
    ]);
}
```
