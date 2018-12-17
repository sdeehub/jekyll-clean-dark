---
layout: post
title: "การใช้ PhpSpreadsheet ร่วมกับ Yii2 (บันทึกความจำ 2/3)"
date: 2018-12-14 11:31:55 +0700
description: ส่วนที่ 2 - ตัวอย่าง Function และ Code ที่ใช้เพื่อเขียนไฟล์ Excel
tags:
  - Yii2
comments: true
---
ลักษณะโจทย์งาน: เขียนงานด้วย PHP โดยใช้ Yii2 Framework - มีการทำฐานข้อมูลให้มี UI ที่หน้าจอ บวกกับอ่านข้อมูลที่เป็นไฟล์ Excel จัดการข้อมูลทำผลลัพธ์ออก UI ที่หน้าจอ และทำผลลัพธ์ออกมาเป็นไฟล์ Excel ด้วย

ข้อมูลอ้างอิงของ PhpSpreadsheet: [PhpSpreadsheet's documentation](https://phpspreadsheet.readthedocs.io/en/develop/)

Model: CreateExcelFile.php

```php
class CreateExcelFile extends \yii\base\Model
{
    public static function forCbdStampingMachining($modelRfqSummary)
    {
        if (! empty($modelRfqSummary->material_spec_1))
        {
            $spreadsheet = \PhpOffice\PhpSpreadsheet\IOFactory::load('template/template_cbd_stamping.xlsx');
            $worksheet = $spreadsheet->getActiveSheet();

            $worksheet->getCell('X2')->setValue($modelRfqSummary->rfq_no);
            $worksheet->getCell('B9')->setValue($modelRfqSummary->drawing_no);
            $worksheet->getCell('D9')->setValue($modelRfqSummary->part_no);
            $worksheet->getCell('G9')->setValue($modelRfqSummary->part_name);
            $worksheet->getCell('K9')->setValue($modelRfqSummary->car_maker);
            $worksheet->getCell('O9')->setValue($modelRfqSummary->car_model);
            $worksheet->getCell('Q9')->setValue($modelRfqSummary->car_series_type);
            $worksheet->getCell('S9')->setValue($modelRfqSummary->application_for);
            $worksheet->getCell('U9')->setValue($modelRfqSummary->fr_rr_type);
            $worksheet->getCell('V9')->setValue($modelRfqSummary->rh_lh_side);
            $worksheet->getCell('W9')->setValue($modelRfqSummary->series_4wd_2wd);
            $worksheet->getCell('X9')->setValue($modelRfqSummary->sop);
            $worksheet->getCell('Y9')->setValue($modelRfqSummary->destination);

            $worksheet->getCell('B12')->setValue($modelRfqSummary->vechal_volume_per_year);
            $worksheet->getCell('D12')->setValue($modelRfqSummary->model_period);
            $worksheet->getCell('G12')->setValue($modelRfqSummary->model_life);
            $worksheet->getCell('I12')->setValue($modelRfqSummary->end_user_customer);
            $worksheet->getCell('S12')->setValue($modelRfqSummary->delivery_place_1);
            $worksheet->getCell('U12')->setValue($modelRfqSummary->delivery_place_2);
            $worksheet->getCell('W12')->setValue($modelRfqSummary->delivery_condition_frequency);

            $worksheet->getCell('G15')->setValue($modelRfqSummary->material_spec_1);

            $worksheet->getCell('D18')->setValue($modelRfqSummary->monthly_used_volume_option_1);
            $worksheet->getCell('G18')->setValue($modelRfqSummary->monthly_used_volume_option_2);
            $worksheet->getCell('K18')->setValue($modelRfqSummary->monthly_used_volume_option_3);
            $worksheet->getCell('O18')->setValue($modelRfqSummary->used_qty_per_1_fg);
            $worksheet->getCell('Q18')->setValue($modelRfqSummary->plating_spec);

            $writer = \PhpOffice\PhpSpreadsheet\IOFactory::createWriter($spreadsheet, 'Xls');
            $writer->save('downloads/cbd_for_suppliers/stamping_machining/'.$modelRfqSummary->rfq_no.'_'.$modelRfqSummary->part_no.'_'.$modelRfqSummary->material_spec_1.'.xls');
        }
        if (! empty($modelRfqSummary->material_spec_2))
        {
            $spreadsheet = \PhpOffice\PhpSpreadsheet\IOFactory::load('template/template_cbd_stamping.xlsx');
            $worksheet = $spreadsheet->getActiveSheet();

            $worksheet->getCell('X2')->setValue($modelRfqSummary->rfq_no);
            $worksheet->getCell('B9')->setValue($modelRfqSummary->drawing_no);
            $worksheet->getCell('D9')->setValue($modelRfqSummary->part_no);
            $worksheet->getCell('G9')->setValue($modelRfqSummary->part_name);
            $worksheet->getCell('K9')->setValue($modelRfqSummary->car_maker);
            $worksheet->getCell('O9')->setValue($modelRfqSummary->car_model);
            $worksheet->getCell('Q9')->setValue($modelRfqSummary->car_series_type);
            $worksheet->getCell('S9')->setValue($modelRfqSummary->application_for);
            $worksheet->getCell('U9')->setValue($modelRfqSummary->fr_rr_type);
            $worksheet->getCell('V9')->setValue($modelRfqSummary->rh_lh_side);
            $worksheet->getCell('W9')->setValue($modelRfqSummary->series_4wd_2wd);
            $worksheet->getCell('X9')->setValue($modelRfqSummary->sop);
            $worksheet->getCell('Y9')->setValue($modelRfqSummary->destination);

            $worksheet->getCell('B12')->setValue($modelRfqSummary->vechal_volume_per_year);
            $worksheet->getCell('D12')->setValue($modelRfqSummary->model_period);
            $worksheet->getCell('G12')->setValue($modelRfqSummary->model_life);
            $worksheet->getCell('I12')->setValue($modelRfqSummary->end_user_customer);
            $worksheet->getCell('S12')->setValue($modelRfqSummary->delivery_place_1);
            $worksheet->getCell('U12')->setValue($modelRfqSummary->delivery_place_2);
            $worksheet->getCell('W12')->setValue($modelRfqSummary->delivery_condition_frequency);

            $worksheet->getCell('G15')->setValue($modelRfqSummary->material_spec_2);

            $worksheet->getCell('D18')->setValue($modelRfqSummary->monthly_used_volume_option_1);
            $worksheet->getCell('G18')->setValue($modelRfqSummary->monthly_used_volume_option_2);
            $worksheet->getCell('K18')->setValue($modelRfqSummary->monthly_used_volume_option_3);
            $worksheet->getCell('O18')->setValue($modelRfqSummary->used_qty_per_1_fg);
            $worksheet->getCell('Q18')->setValue($modelRfqSummary->plating_spec);

            $writer = \PhpOffice\PhpSpreadsheet\IOFactory::createWriter($spreadsheet, 'Xls');
            $writer->save('downloads/cbd_for_suppliers/stamping_machining/'.$modelRfqSummary->rfq_no.'_'.$modelRfqSummary->part_no.'_'.$modelRfqSummary->material_spec_2.'.xls');
        }
    }
}
```
