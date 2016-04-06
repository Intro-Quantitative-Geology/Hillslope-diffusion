# Fixing Spyder
By default, plots in **Spyder** appear in the IPython console and their resolution is not as good as plots in a separate plot window. To fix this you need to first fix the preferences in **Spyder**, then change the plotting preference.

## Fixing the Spyder preferences
The preferences in **Spyder** can be fixed by doing the following:

1. Close **Spyder**, if it is open.
2. In a Terminal, enter the following:

    ```bash
    $ conda install colorama=0.3.3
    ```
    When prompted, enter `y` for whether or not to downgrade colorama.
3. Once the downgrade is complete, open **Spyder** again.

    ```bash
    $ spyder
    ```
The preferences should now be working.

## Changing plot preferences to appear in separate window
- Open Spyder Preferences
- Select IPython console from list on left, then click on the Graphics tab
- Change Backend to Automatic
- Close and re-open Spyder
