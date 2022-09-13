# OpenCV Object Tracking in TouchDesigner
This component for object tracking made with OpenCV allows the detection of multiple objects with a non-commercial license of TouchDesigner.

## Input data
- `Video` | The component requires a TOP to analyze
- `Threshold` | The amount of threshold applied to the input video
- `MinArea` | The minimum area of an object
- `MaxArea` | The maximum area of an object
- `ResetIDs` | A pulse button that resets the ID count

## Output data
The component has 2 outputs:
- A table with all the global data (first 2 rows) and data for each object.
- A TOP with boxes and IDs drown over each detected object.
  
>**In some versions of TouchDesigner it may be necessary to attach a null TOP to the output for the component to work**

### Global data
The output data is updated every frame. When no blobs are detected the average position defaults to 0.5, 0.5
- `NumOfBlobs` | How many objects are detected
- `AvgX` | The average horizontal position of all the objects detected. This value is normalized in a range between 0 (left) and 1 (right).
- `AvgY` | The average vertical position of all the objects detected. This value is normalized in a range between 0 (bottom) and 1 (top).

### Blob data
All the data of individual objects are in pixels
- `ID` | The unique number of the object. IDs are created sequentially and automatically reset when no objects are detected or when the reset button is pressed.
- `X` | The horizontal position of the object
- `Y` | The vertical position of the object
- `Width` | The width of the object
- `Height` | The height of the object


## Customization
### Minimum distance between objects
To change the minimum distance between two objects to be detected go to the **main_script** node and change the number on line **26**.

```
if dist < 50:  # <-------- Minimum distance between objects
  self.center_points[id] = (cx, cy)
  objects_bbs_ids.append([x, y, w, h, id])
  same_object_detected = True
  break
```