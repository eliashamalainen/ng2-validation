# Description

Angular2 custom validation, inspired by jQuery validation.

# Install

```bash
npm install ng2-validation --save
```

# Validators

## angular2 built-in validators

- required
- minlength
- maxlength
- pattern

## extend validators

- rangeLength
- min
- max
- range
- digits
- number
- url
- email
- date
- dateISO
- creditCard
- json
- base64
- phone
- uuid
- equal
- equalTo

# Usage

## template driven

import `FormsModule` and `CustomFormsModule` in *app.module.ts*

```javascript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule } from '@angular/forms';
import { CustomFormsModule } from 'ng2-validation'

import { AppComponent } from './app.component';

@NgModule({
    imports: [BrowserModule, FormsModule, CustomFormsModule],
    declarations: [AppComponent],
    bootstrap: [AppComponent]
})
export class AppModule {
}
```

### rangeLength

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" [rangeLength]="[5, 9]"/>
<p *ngIf="field.errors?.rangeLength">error message</p>
```

### min

```html
<input type="number" [(ngModel)]="model.field" name="field" #field="ngModel" [min]="10"/>
<p *ngIf="field.errors?.min">error message</p>
```

### max

```html
<input type="number" [(ngModel)]="model.field" name="field" #field="ngModel" [max]="20"/>
<p *ngIf="field.errors?.max">error message</p>
```

### range

```html
<input type="number" [(ngModel)]="model.field" name="field" #field="ngModel" [range]="[10, 20]"/>
<p *ngIf="field.errors?.range">error message</p>
```

### digits

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" digits/>
<p *ngIf="field.errors?.digits">error message</p>
```

### number

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" number/>
<p *ngIf="field.errors?.number">error message</p>
```

### url

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" url/>
<p *ngIf="field.errors?.url">error message</p>
```

### email

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" email/>
<p *ngIf="field.errors?.email">error message</p>
```

### date

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" date/>
<p *ngIf="field.errors?.date">error message</p>
```

### dateISO

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" dateISO/>
<p *ngIf="field.errors?.dateISO">error message</p>
```

### creditCard

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" creditCard/>
<p *ngIf="field.errors?.creditCard">error message</p>
```

### json

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" json/>
<p *ngIf="field.errors?.json">error message</p>
```

### base64

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" base64/>
<p *ngIf="field.errors?.base64">error message</p>
```

### phone

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" [phone]="'zh-CN'"/>
<p *ngIf="field.errors?.phone">error message</p>
```

*default*: en-US

**support**

- zh-CN
- zh-TW
- en-ZA
- en-AU
- en-HK
- fr-FR
- pt-PT
- el-GR
- en-GB
- en-US
- en-ZM
- ru-RU
- nb-NO
- nn-NO
- vi-VN
- en-NZ

### uuid

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" [uuid]="'all'"/>
<p *ngIf="field.errors?.uuid">error message</p>
```

*default*: all

**support**

- 3
- 4
- 5
- all

### equal

```html
<input type="text" [(ngModel)]="model.field" name="field" #field="ngModel" [equal]="'xxx'"/>
<p *ngIf="field.errors?.equal">error message</p>
```

### equalTo

```html
<form #demoForm="ngForm" novalidate>
  <div ngModelGroup="passwordGroup" equalTo>
    <input type="password" ngModel name="password" #password="ngModel" required/>
    <p *ngIf="password?.errors?.required">required error</p>
    <input type="password" ngModel name="certainPassword"/>
    <p *ngIf="demoForm.form.controls.passwordGroup?.errors?.equalTo">equalTo error</p>
  </div>
</form>
```

## model driven

import `ReactiveFormsModule` in *app.module.ts*

```javascript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { ReactiveFormsModule } from '@angular/forms';

import { AppComponent } from './app.component';

@NgModule({
    imports: [BrowserModule, ReactiveFormsModule],
    declarations: [AppComponent],
    bootstrap: [AppComponent]
})
export class AppModule {
}
```

import `CustomValidators` in *app.component.ts*

```javascript
import { Component } from '@angular/core';
import { FormGroup, FormControl } from '@angular/forms';
import { CustomValidators } from 'ng2-validation';

@Component({
    selector: 'app',
    template: require('./app.html')
})
export class AppComponent {
    form: FormGroup;

    constructor() {
        this.form = new FormGroup({
            field: new FormControl('', CustomValidators.range([5, 9]))
        });
    }
}
```

```html
<input type="text" formControlName="field"/>
<p *ngIf="demoForm.from.controls.field.errors?.rangeLength">error message</p>
```

### rangeLength

```javascript
new FormControl('', CustomValidators.rangeLength([5, 9]))
```

### min

```javascript
new FormControl('', CustomValidators.min(10))
```

### max

```javascript
new FormControl('', CustomValidators.max(20))
```

### range

```javascript
new FormControl('', CustomValidators.range([10, 20]))
```

### digits

```javascript
new FormControl('', CustomValidators.digits)
```

### number

```javascript
new FormControl('', CustomValidators.number)
```

### url

```javascript
new FormControl('', CustomValidators.url)
```

### email

```javascript
new FormControl('', CustomValidators.email)
```

### date

```javascript
new FormControl('', CustomValidators.date)
```

### dateISO

```javascript
new FormControl('', CustomValidators.dateISO)
```

### creditCard

```javascript
new FormControl('', CustomValidators.creditCard)
```

### json

```javascript
new FormControl('', CustomValidators.json)
```

### base64

```javascript
new FormControl('', CustomValidators.base64)
```

### phone

```javascript
new FormControl('', CustomValidators.phone('zh-CN'))
```

### uuid

```javascript
new FormControl('', CustomValidators.uuid('3'))
```

### equal

```javascript
new FormControl('', CustomValidators.equal('xxx'))
```

### equalTo

```javascript
@Component({
  selector: 'app',
  template: require('./app.html')
})
export class AppComponent implements OnInit {
  form: FormGroup;
  
  ngOnInit() {
    var password = new FormControl('', Validators.required);
    var certainPassword = new FormControl('');

    this.form = new FormGroup({
      passwordGroup: new FormGroup({
        password: password,
        certainPassword: certainPassword
      }, CustomValidators.equalTo)
    });
  }
}
```

```html
<form [formGroup]="form" novalidate>
  <div formGroupName="passwordGroup">
    <input type="password" formControlName="password"/>
    <p *ngIf="form.controls.passwordGroup.controls.password?.errors?.required">required error</p>
    <input type="password" formControlName="certainPassword"/>
    <p *ngIf="form.controls.passwordGroup?.errors?.equalTo">equalTo error</p>
  </div>
  <button>submit</button>
</form>
```

# License

MIT