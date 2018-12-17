---
layout: post
title: "การใช้ PhpSpreadsheet ร่วมกับ Yii2 (บันทึกความจำ 3/3)"
date: 2018-12-14 11:21:55 +0700
description: ตัวอย่างงานแสดงผล HTML จากไฟล์ Excel
tags:
  - Yii2
comments: true
---
ลักษณะโจทย์งาน: เขียนงานด้วย PHP โดยใช้ Yii2 Framework - มีการทำฐานข้อมูลให้มี UI ที่หน้าจอ บวกกับอ่านข้อมูลที่เป็นไฟล์ Excel จัดการข้อมูลทำผลลัพธ์ออก UI ที่หน้าจอ และทำผลลัพธ์ออกมาเป็นไฟล์ Excel ด้วย

ข้อมูลอ้างอิงของ PhpSpreadsheet: [PhpSpreadsheet's documentation](https://phpspreadsheet.readthedocs.io/en/develop/)

Views: cbd-stamping-machining/form_general.php

```html
<div class="cbd-stamping-machining-form">

    <?php $form = ActiveForm::begin(); ?>

    <div class="row">
        <div class="col-sm-6 col-md-4">
            <?= $form->field($model, 'supplier_name')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-6 col-md-4">
            <?= $form->field($model, 'supplier_address')->textArea(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'supplier_tel')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'supplier_fax')->textInput(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-6 col-md-4">
            <?= $form->field($model, 'quotation_number')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-6 col-md-4">
            <?= $form->field($model, 'quotation_period')->textInput(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'sale_person_in_charge')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'email')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'mobile_phone')->textInput(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-6 col-md-4">
            <?= $form->field($model, 'boi')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-6 col-md-4">
            <?= $form->field($model, 'non_boi')->textInput(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'incor_team')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'mass_pro_tooling_lead_time')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'tooling_design_type')->textInput(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-6 col-md-4">
            <?= $form->field($model, 'process')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-6 col-md-4">
            <?= $form->field($model, 'm_c_size')->textInput(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'capacity_per_day')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'capacity_per_month')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'working_day')->textInput(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'shift')->textInput() ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'moq_snp')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'guarantee_short_qty')->textInput(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'prototype_tooling_lt')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'rack_barrel')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'lot_frequency_min')->textInput(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'plating_vendor_name')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'location')->textInput(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-6 col-md-4">
            <?= $form->field($model, 'tooling_design_by')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-6 col-md-4">
            <?= $form->field($model, 'tooling_design_by_address')->textArea(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-6 col-md-4">
            <?= $form->field($model, 'tooling_produce_by')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-6 col-md-4">
            <?= $form->field($model, 'tooling_produce_by_address')->textArea(['maxlength' => true]) ?>
        </div>
    </div>
    <div class="row">
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'prepared_by')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'supervisor')->textInput(['maxlength' => true]) ?>
        </div>
        <div class="col-sm-4 col-md-3">
            <?= $form->field($model, 'manager')->textInput(['maxlength' => true]) ?>
        </div>
    </div>

    <div class="form-group">
        <?= Html::submitButton('Save', ['class' => 'btn btn-success']) ?>
    </div>

    <?php ActiveForm::end(); ?>

</div>
```
