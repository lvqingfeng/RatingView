# RatingView

![alt tag](https://i.imgur.com/hgC7q3I.png)

Example:

![alt tag](https://i.imgur.com/BkGt9Jz.png)

Android view for showing rating or quiz results

Connecting via downloading 
----------

You can add the library to your project using Gradle.
1) Copy the **RatingView** directory to your project's directory;
2) Find the **settings.gradle** file. Most likely, it contains something like that:

```gradle
include ':app'
```

Edit the line this way:

```gradle
include ':app', ':ratingview'
```

3) Add this line to your dependencies in your app's gradle:

```gradle
compile project(':ratingview')
```

### Usage

Add `RatingView` to your layout:
```xml
 <com.nefrit.ratingview.gui.RatingView
            android:id="@+id/view_rating"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"/>
```

You can also add `RatingView` via constuctor: 
```java
RatingView ratingView = new RatingView(context);
List<Scale> scales = new ArrayList<>();
scales.add(new Scale("Yes", 492, getResources().getColor(R.color.mark_green)));
scales.add(new Scale("No", 224, getResources().getColor(R.color.mark_red)));
scales.add(new Scale("Neutral", 7, getResources().getColor(R.color.mark_yellow)));

ratingView.setScales(scales);
container.addView(ratingView);
```

### Class Scale

You'll need at least one `Scale` object to make your `RatingView` works.

Then set scales to your `RatingView` using method: 
```java
ratingView.setScales(scales);
```
`RatingView` transforms every `Scale` to `RatingItem`, which is View. See below.

### View RatingItem

You can get `RatingItem` from your `RatingView` using: 
```java
RatingItem ratingItem = ratingView.getRatingItem(position);
ratingItem.setProgressColor(Color.RED);         // Change progress color
ratingItem.setMarksValue("Cool");       // Change mark text
ratingItem.setScale(scale);     // Change the whole scale (mark text, marks count and progress color)
```

Take a look at the [sample project](sample) for more information.