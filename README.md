# Vue-Image-Upload

### You have to just follow a few steps to get following Vue-Image-Upload services


## Getting Started
### Step 1: install this npm package

```` 
npm install object-to-formdata

````

## Step 2:Import objectFormData import on file.

````
import{objectToFormData} from 'object-to-formData'

````

## Step 3:Catch image file and save image  .

````
onImageChange(e){
    const file = e.target.files[0]
    this.productForm.image = file
}

````

## Step 4:Passing object sothat convart this image and add to formData.

````
this.productForm.post('/api/product',{
  transformRequest:[function(data,headers){
      return objectToFormData(data)
  }],
  onUploadProgress: e =>{
      console.log(e)
  }
}).then(({data})=>{
  console.log(data);
  // this.productForm.name = '';
  // this.productForm.status = false;
  this.$swal.fire(
      'Done!',
      'product Create Successfully!',
      'success'
  );

````

## Step 5:On template file use @change method.

````
<div class="col-md-10">
    <div class="form-group">
       <label for="Image">Image</label>
       <div class="input-group">
          <div class="custom-file">
             <input type="file" @change="onImageChange" name="image" class="custom-file-input" id="Image">
             <label class="custom-file-label" for="Image">Choose Image</label>
          </div>
       </div>
    </div>
 </div>

````

## Step 6:Work backend on controller.

````
$product = new Product();

if($request->image){
    $imageName = time().'-'.uniqid().'.'.$request->image->getClientOriginalExtension();
    $request->image->move(public_path('storage/product/'),$imageName);
    $product->image = '/storage/product/'.$imageName;
}
$product->save();
return response()->json(['success','product'=>$product,200]);
 
````

## Step 7:if this package does not work go package.json

```
"object-to-formdata": "^4.1.0", 
to
"object-to-formdata": "^3.0.9", ->save

cmd->npm install
cmd->npm audit fix
and overwrite this package
````
## Step 7:Yeap! it's finished and good luck.

```
if you have face any kind of problem for this step go to www.github.com/contactmithuroy/Vue-Image-Upload to product create file or follwow https://youtu.be/oZU6jmrXgxE?list=PLl4v4A2HI0YhuNkhyK1E5WcDGiXr-zBgc this youtube channel

````

