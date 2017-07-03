> 以前一直都是用Picasso将图片设置在imageView上面，今天有个项目需求，是将imageView设置在layout的background上面，特意查了一下，现在打算记录一下。

```
picasso一般的用法

Picasso
                .with(mContext)
                .load(url)
                .fit()
                .centerCrop()
                .into(holder.imageView);
```

----

如果想将图片设置在其它地方：

```

Picasso.with(this).load("http://imageUrl").into(new Target() {
            @Override
            public void onBitmapLoaded(Bitmap bitmap, Picasso.LoadedFrom from) {
               mYourLayout.setBackground(new BitmapDrawable(bitmap));
            }

            @Override
            public void onBitmapFailed(Drawable errorDrawable) {

            }

            @Override
            public void onPrepareLoad(Drawable placeHolderDrawable) {

            }
        });

```


或者采用：

```

ImageView img = new ImageView(this);
               Picasso.with(this)
              .load(imageUri)
              .fit()
              .centerCrop()
              .into(img, new Callback() {
                        @Override
                        public void onSuccess() {

                            myLayout.setBackgroundDrawable(img.getDrawable());
                        }

                        @Override
                        public void onError() {

                        }
                    });
```


that's all.
