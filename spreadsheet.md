# Worked example

There are so many different spreadsheet applications that we couldn't possibly provide guides for them all. Instead, we've provided a worked example for how to get going using some free software called [LibreOffice](https://www.libreoffice.org/) that's preinstalled on the Raspberry Pi operating system (Raspbian).

![](images/LibreOffice_logo.png)

## Raspbian

Before doing anything it's advisable to [download](https://www.raspberrypi.org/downloads/) the latest version of Raspbian *Jessie* and install it on your SD card. If you need help with this please read our [NOOBS setup guide](https://www.raspberrypi.org/help/noobs-setup/). Note that the video shows Raspbian *Wheezy* being installed. The Wheezy version is now out of date and does not come with LibreOffice but Jessie does.

Boot up your Raspberry Pi as usual using your new Raspbian Jessie SD card.

## Download the CSV zip file

Currently only the example data is available. This data was *not* recorded in space; it was captured at an office desk in Cambridge. Don't spend too much effort analysing it; it's only been provided so that you can examine the file layout and check that you can load it properly. The file you'll get from the ISS will use the same format and layout.

You can download the [example CSV here](https://github.com/raspberrypilearning/astro-pi-flight-data-analysis/blob/master/data/astro_pi_data_20150824_085954.zip?raw=true).

After downloading the zip file, open the *File Manager* application and navigate to the `Downloads` folder. The zip file should be shown on the right:

![](images/ex01.png)

Right-click on the zip file and select `Extract Here` from the context menu.

![](images/ex02.png)

The CSV file containing the data should now appear.

## Load the CSV into LibreOffice

Right-click on the CSV file and select `LibreOffice Calc` from the context menu.

![](images/ex03.png)

The following dialogue will appear. This allows you to configure how LibreOffice Calc should import the data; the default options are fine so just click the OK button.

![](images/ex04.png)

The data will now show in the usual tabular spreadsheet layout.

## Copy data to work on

It is likely that the CSV file will contain more than 30,000 rows, possibly more depending on how long Tim Peake leaves the Astro Pis in flight recorder mode. This amount of data can cause LibreOffice Calc to run *very slowly*, especially when producing graphs; this will be very noticeable if you're using older models of the Raspberry Pi. So for this exercise, we're going to select the first 500 rows and copy them into a new spreadsheet to work on. This will be a lot faster.

Start by clicking in the margin where the red star is shown below to select an entire row. Then hold down the shift key and use the down arrow key to select more rows.

![](images/ex05.png)

Keep going until you reach the 500th row.

![](images/ex06.png)

Then right-click on the selected rows, as shown by the red star above, and select `Copy` from the context menu.

![](images/ex07.png)

Click on the green `+` symbol at the bottom of the program to create a new blank sheet.

![](images/ex08.png)

From the `Edit` menu at the top, select `Paste`.

![](images/ex09.png)

The copied data should then appear.

![](images/ex10.png)

Working with only 500 rows will be a lot quicker and more responsive, allowing you to get to grips with LibreOffice Calc without having long processing delays between each step.

## Format the timestamp column

Currently, the timestamp column is in *text* format. If you want to use this in any calculations, such as working out the time between two rows, then you'll need to format the entire column as a *time*. So let's do this now before we go any further.

Scroll to the right and find column `T`, which should be `time_stamp`. Right-click on the column header and select `Format Cells` from the context menu.

![](images/ex11.png)

On the `Numbers` tab select `Time` under `Category`, and then under `Format` choose the last option in the list that says `1999-12-31 13:37:46`.

![](images/ex12.png)

Check that the format code is the same as in the picture above, then click OK.

## Plot humidity

To gain some familiarity with making charts we're going to examine humidity versus time, as if we're looking for crew activity near the Astro Pis. Feel free to use a different sensor if you prefer. Time will be on the horizontal X axis and the humidity will be on the vertical Y axis. Scroll back to the left and find column `E` which should be `humidity`, then left-click on the column header (shown by the red star below) to select all rows in the column. Next, click the `Chart` button in the toolbar.

![](images/ex13.png)

The Chart Wizard will now show. Under `Chart Type` select `Line` followed by `Lines Only`, then select Step 3 (Data Series) from the left-hand menu.

![](images/ex14.png)

Below `Data series`, `humidity` should be selected; under `Data ranges` select `Y-Values`. You'll now see that the `Categories` box is empty. This box allows you to specify the corresponding horizontal X axis values for the humidity on the Y axis.

We saw from before that the timestamp data is in column `T`, so enter `$Sheet2.$T$2:$T$500` to specify rows 2 to 500 and click Next. It can be quicker to copy and paste the text inside the `Range for Y-Values` field above, and just change the letter `E` to `T` in both places.

![](images/ex15.png)

Step 4 (Chart Elements) just allows you to specify titles for the axes and for the chart itself; you can skip this if you want to.

![](images/ex16.png)

When you're ready click Finish.

## Examine the chart

You can expand the chart by clicking and dragging the resize zones on the edges and corners.

![](images/ex17.png)

Notice that the Y axis doesn't start at zero, so even though it looks like the relative humidity is changing a lot here it's only varying by around 3%, which isn't that much. This is what you might expect at an office desk over the course of an hour or so.

## Deleting charts

If you're not happy with how a chart has come out you might want to delete it and try again. To delete a chart you simply select it and press the `Delete` key on your keyboard.

![](images/exDel.png)

If you see the error message above it's because you still have the column selected in addition to the chart. To handle this, just click on any cell in the spreadsheet and then reselect the chart before trying to delete it again.

## Add more data

Let's say you now wanted to look for CHX dry-outs and need both temperature and humidity on the same chart. The process is essentially the same as before, but instead of only selecting one column at the start, you hold down the `Ctrl` key and select as many as you like before clicking the `Chart` button.

![](images/ex18.png)

This time the Y axis does start from zero, meaning that you're seeing a much more accurate depiction of the measurements. Once you feel confident you can go back to the original CSV data and try to load more than 500 rows into a chart. Be wary of doing this for all rows as it will be very slow!

Good luck!

[LibreOffice Calc Online Help](https://help.libreoffice.org/Calc/Welcome_to_the_Calc_Help)

[< Back to the worksheet](worksheet.md#how-do-i-analyse-the-data)
