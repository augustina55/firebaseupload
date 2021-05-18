# firebaseupload


Firebase image upload and get Download url

//Add this Code

          ref.putFile(filepath).addOnSuccessListener(new OnSuccessListener<UploadTask.TaskSnapshot>() {
                @Override
                public void onSuccess(UploadTask.TaskSnapshot taskSnapshot) {
                    //Image uploaded
                    //GetdownloadURl here
                    strg.child("Pic").getDownloadUrl().addOnCompleteListener(new OnCompleteListener<Uri>() {
                        @Override
                        public void onComplete(@NonNull Task<Uri> task) {
                            //getdownloadUrl
                            downloadUrl=task.getResult().toString();
                            dbref.push().child("imageurl").setValue(downloadUrl);
                            progressDialog.dismiss();
                            Toast.makeText(MainActivity.this,"Image uploaded",Toast.LENGTH_LONG).show();
                        }
                    });
                }
            });
