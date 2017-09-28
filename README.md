![screen shot 2017-01-22 at 14 07 50](https://cloud.githubusercontent.com/assets/1526680/22182355/31d103ca-e0ac-11e6-9664-c7c0399ef69f.png)

## Installing

```bash
$ npm install --save ngx-mask
```

## Quickstart

Import **ngx-mask** module in Angular app.

```typescript
import {NgxMaskModule} from 'ngx-mask'

(...)

@NgModule({
  (...)
  imports: [
    NgxMaskModule.forRoot(options)
  ]
  (...)
})
```

Then, just define masks in inputs.

#### Usage

```html 
<input type='text' mask='{here comes your mask}' >
```

#### Examples

| mask | example |
| ------- | ------- |
| 9999-99-99 | 2017-04-15 |
| 000.000.000-99 | 048.457.987-98 |
| AAAA | 0F6g |
| SSSS | asDF |

## Mask Options 
You can define your custom options for hole directives (as options object in the mask module) or per each (as attributes for directive)
### specialCharacters (string[ ]) 
 We have next default characters:
   
   | character |
   |-----------|
   | / | 
   | ( | 
   | ) |
   | . |
   | : |
   | - |
   | **space** |
   | + | 
   
##### Usage

```html 
<input type='text' specialCharacters="[ '[' ,']' , '*' ]" mask="[00]*[000]" >
```

##### Then:

```
Input value: 789-874.98
Masked value: [78]*[987]
```
   
### patterns ({ [character: string]: { pattern: RegExp, optional?: boolean})
   We have next default patterns:
   
  | code | meaning |
  |------|---------|
  | **0** | digits (like 0 to 9 numbers) |
  | **0** | digits (like 0 to 9 numbers), but optional |
  | **A** | letters (uppercase or lowercase) and digits |
  | **S** | only letters (uppercase or lowercase) |
  
```html 
<input type='text' patterns="{'0': { pattern: new RegExp('\[a-zA-Z\]')}}" mask="(000-000)" >
```

##### Then:

```
Input value: 789HelloWorld
Masked value: (Hel-loW)
```

### dropSpecialCharacters (boolean) 
   You can choose if mask will drop special character in the model, or not, default value true
##### Usage

```html 
<input type='text' dropSpecialCharacters="false" mask="000-000.00" >
```

##### Then:

```
Input value: 789-874.98
Model value: 789-874.98
```

### clearIfNotMatch (boolean)    
   You can choose clear the input if the input value **not match** the mask, default value false 


## Examples

Check the [demo](https://nepipenkoigor.github.io/ngx-mask/).
