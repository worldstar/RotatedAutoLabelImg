RotatedAutoLabelImg
==========

.. image:: https://img.shields.io/pypi/v/labelimg.svg
        :target: https://pypi.python.org/pypi/labelimg

.. image:: https://img.shields.io/travis/tzutalin/labelImg.svg
        :target: https://travis-ci.org/tzutalin/labelImg

RotatedAutoLabelImg 是一款圖形化的圖像自動化標註工具，可以自動識別並標註，是基於原始版本「roLabelImg」的重寫版本，並且加上了YOLOv8 OBB。

原始版本「roLabelImg」的鏈接在這裡：https://github.com/cgvict/roLabelImg。

「YOLOv8 OBB」的連結在這裡 : https://github.com/orgs/ultralytics/discussions/7472。

它使用 Python 編寫，並採用了 Qt 作為其圖形界面框架。

.. roLabelImg is a graphical image annotation tool can label ROTATED rectangle regions, which is rewrite from 'labelImg'.

.. The original version 'labelImg''s link is here<https://github.com/tzutalin/labelImg>.

.. It is written in Python and uses Qt for its graphical interface.

`接下來請看範例`

自動標註有3種功能

+------------+--------------------------------------------+
| 標註並下一張| 自動標註當前圖片後切換至下一張圖片            |
+------------+--------------------------------------------+
| 標註這張    | 將當前圖片進行自動標註                       |
+------------+--------------------------------------------+
| 自動標註    | 將當前資料夾裡的所有圖片全部自動標註          |
+------------+--------------------------------------------+

.. `Watch a demo by author cgvict`

.. image:: https://github.com/worldstar/RotatedAutoLabelImg/blob/master/demo/redemo1.png
     :alt: Demo Image

.. image:: https://raw.githubusercontent.com/cgvict/roLabelImg/master/demo/demo_v2.5.gif

https://youtu.be/7D5lvol_QRA

註釋會被保存為 XML 文件，格式類似於 PASCAL VOC 格式，這是 ImageNet <http://www.image-net.org/>__ 使用的格式。

.. Annotations are saved as XML files almost like PASCAL VOC format, the format used by `ImageNet <http://www.image-net.org/>`__.


XML 格式
------------------

.. code::

    <annotation verified="yes">
      <folder>hsrc</folder>
      <filename>100000001</filename>
      <path>/Users/haoyou/Library/Mobile Documents/com~apple~CloudDocs/OneDrive/hsrc/100000001.bmp</path>
      <source>
        <database>Unknown</database>
      </source>
      <size>
        <width>1166</width>
        <height>753</height>
        <depth>3</depth>
      </size>
      <segmented>0</segmented>
      <object>
        <type>bndbox</type>
        <name>ship</name>
        <pose>Unspecified</pose>
        <truncated>0</truncated>
        <difficult>0</difficult>
        <bndbox>
          <xmin>178</xmin>
          <ymin>246</ymin>
          <xmax>974</xmax>
          <ymax>504</ymax>
        </bndbox>
      </object>
      <object>
        <type>robndbox</type>
        <name>ship</name>
        <pose>Unspecified</pose>
        <truncated>0</truncated>
        <difficult>0</difficult>
        <robndbox>
          <cx>580.7887</cx>
          <cy>343.2913</cy>
          <w>775.0449</w>
          <h>170.2159</h>
          <angle>2.889813</angle>
        </robndbox>
      </object>
    </annotation>


安裝

.. Installation
------------------

Download prebuilt binaries of original 'labelImg'
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  `Windows & Linux <http://tzutalin.github.io/labelImg/>`__

-  OS X. Binaries for OS X are not yet available. Help would be appreciated. At present, it must be `built from source <#os-x>`__.

從源碼構建

.. Build from source
~~~~~~~~~~~~~~~~~

Linux/Ubuntu/Mac requires at least `Python
2.6 <http://www.python.org/getit/>`__ and has been tested with `PyQt
4.8 <http://www.riverbankcomputing.co.uk/software/pyqt/intro>`__.


Ubuntu Linux
^^^^^^^^^^^^

.. code::

    sudo apt-get install pyqt4-dev-tools
    sudo pip install lxml
    make all
    ./roLabelImg.py
    ./roLabelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]

OS X
^^^^

.. code::

    brew install qt qt4
    brew install libxml2
    make all
    ./roLabelImg.py
    ./roLabelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]

Windows
^^^^^^^

Download and setup `Python 2.6 or
later <https://www.python.org/downloads/windows/>`__,
`PyQt4 <https://www.riverbankcomputing.com/software/pyqt/download>`__
and `install lxml <http://lxml.de/installation.html>`__.

打開命令行並進入 'roLabelImg <#roLabelimg>'__ 目錄

.. Open cmd and go to `roLabelImg <#roLabelimg>`__ directory

.. code::

    pyrcc4 -o resources.py resources.qrc
    python roLabelImg.py
    python roLabelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]

Use Docker
~~~~~~~~~~~~~~~~~
.. code::

    docker pull tzutalin/py2qt4

    docker run -it \
    --user $(id -u) \
    -e DISPLAY=unix$DISPLAY \
    --workdir=$(pwd) \
    --volume="/home/$USER:/home/$USER" \
    --volume="/etc/group:/etc/group:ro" \
    --volume="/etc/passwd:/etc/passwd:ro" \
    --volume="/etc/shadow:/etc/shadow:ro" \
    --volume="/etc/sudoers.d:/etc/sudoers.d:ro" \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    tzutalin/py2qt4

您可以提取包含所有已安裝和所需相依套件的圖片檔。

.. You can pull the image which has all of the installed and required dependencies.  

使用方法
-----

步驟
~~~~~

手動標註

1. 按照上述指示建置並啟動。
2. 在選單「檔案」中點擊 「更改預設儲存標註資料夾」。
3. 點擊 「開啟資料夾」。
4. 點擊 「建立矩形框」。
5. 按下並釋放左鍵，選取要標註的矩形區域。
6. 您可以使用右鍵拖動矩形框來複製或移動它。

自動標註

1. 按照上述指示建置並啟動。
2. 在選單「檔案」中點擊 「更改預設儲存標註資料夾」。
3. 點擊 「標註並下一張」或「標註這張」或「自動標註」。
4. 等待生成。
5. 您可以使用左鍵移動，右鍵旋轉矩形框或複製它。

.. 1. Build and launch using the instructions above.
.. 2. Click 'Change default saved annotation folder' in Menu/File
.. 3. Click 'Open Dir'
.. 4. Click 'Create RectBox'
.. 5. Click and release left mouse to select a region to annotate the rect
   box
.. 6. You can use right mouse to drag the rect box to copy or move it

The annotation will be saved to the folder you specify.

You can refer to the below hotkeys to speed up your workflow.

Create pre-defined classes
~~~~~~~~~~~~~~~~~~~~~~~~~~

You can edit the
`data/predefined\_classes.txt <https://github.com/tzutalin/labelImg/blob/master/data/predefined_classes.txt>`__
to load pre-defined classes

Hotkeys
~~~~~~~

+------------+--------------------------------------------+
| Ctrl + u   | Load all of the images from a directory    |
+------------+--------------------------------------------+
| Ctrl + r   | Change the default annotation target dir   |
+------------+--------------------------------------------+
| Ctrl + s   | Save                                       |
+------------+--------------------------------------------+
| Ctrl + d   | Copy the current label and rect box        |
+------------+--------------------------------------------+
| Space      | Flag the current image as verified         |
+------------+--------------------------------------------+
| w          | Create a rect box                          |
+------------+--------------------------------------------+
| e          | Create a Rotated rect box                  |
+------------+--------------------------------------------+
| d          | Next image                                 |
+------------+--------------------------------------------+
| a          | Previous image                             |
+------------+--------------------------------------------+
| r          | Hidden/Show Rotated Rect boxes             |
+------------+--------------------------------------------+
| n          | Hidden/Show Normal Rect boxes              |
+------------+--------------------------------------------+
| del        | Delete the selected rect box               |
+------------+--------------------------------------------+
| Ctrl++     | Zoom in                                    |
+------------+--------------------------------------------+
| Ctrl--     | Zoom out                                   |
+------------+--------------------------------------------+
| ↑→↓←       | Keyboard arrows to move selected rect box  |
+------------+--------------------------------------------+
| zxcv       | Keyboard to rotate selected rect box       |
+------------+--------------------------------------------+

How to contribute
~~~~~~~~~~~~~~~~~

Send a pull request

License
~~~~~~~
`Free software: MIT license <https://github.com/cgvict/roLabelImg/blob/master/LICENSE>`_


Related
~~~~~~~

1. `ImageNet Utils <https://github.com/tzutalin/ImageNet_Utils>`__ to
   download image, create a label text for machine learning, etc
2. `Docker hub to run it <https://hub.docker.com/r/tzutalin/py2qt4>`__
