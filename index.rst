==================================
Encouragement of porting Python 3 
==================================

Preface はじめに
================

先ほど、お昼休みに交わされた時の会話

   - よ「LT するんですか？何の話するんですか？」
   - な「Python3 の porting の話だよ」
   - よ「えっ、 @aodag さんの前で？」
   - な「いーじゃん」


Profile （おまえ誰よ）
======================

* Hajime Nakagami
   - @hajime_nakagami

   .. image :: nakagami.png

   - A Python/Django programmer
   - BeProud inc.

To do for Python community
=====================================

* Join a User Group ( PyJUG )
* 勉強会に参加する
* Event staff ( PyCon JP 2012 )
* Document writing
* Document translating to Japanese
* Development
   - Web Application Framework
   - Database driver
   - O/R Mapper
   - Another category tools & libralies
   - Porting from Python2 to Python3

Why now ?
==========

Python 3.3 can use u"" literal.

Python3 ::

   "あいうえお" == u"あいうえお"
   "abc".encode('utf-8') ==  b"abc"

Python2 ::

    "abc" == b"abc"
    u"あいうえお".encode('utf-8') == "あいうえお"

Document about porting
=======================

* Porting Python 2 Code to Python 3
   http://docs.python.org/py3k/howto/pyporting.html
* Porting Extension Modules to Python3
   http://docs.python.org/py3k/howto/cporting.html
* ライブラリをPython3対応に書き換える（清水川Web）
   http://www.freia.jp/taka/blog/768/index.html
* BP Study #54 そろそろ Python3  (by @aodag)
   http://www.slideshare.net/aodag/bpstudy54-python3


Let's try
=========

continue my case

Case Study: ReportLab
========================

* ReportLab ( Python library for generating PDFs.)
   http://pypi.python.org/pypi/reportlab
* My Repository ( start from Reportlab 2.5 tarball )
   https://github.com/nakagami/reportlab

::

   $ git clone git://github.com/nakagami/reportlab.git
   $ cd reportlab/tests
   $ python3 runAll.py

Case Study 2: Pillow (PIL)
==========================

* Pillow ( Python Image Library fork )
   https://github.com/python-imaging/Pillow
* My Repository ( fork from Pillow repository )
   https://github.com/nakagami/Pillow

::

   $ git clone git://github.com/nakagami/Pillow.git
   $ cd Pillow
   $ git checkout py33py27
   $ rm -rf build dist
   $ python3 setup.py install
   $ python3 selftests.py

感想
====

* 正直、飽きてきた
* 最初いろいろ動かないが、途中からは同じパターンの繰り返し
* 古くからあるものは書き方が古くて移植しづらい
* 文字列と UNICODE 文字列の扱いがごちゃごちゃなものは難しい
* Python2.7 でも動くように維持した方が移植が楽
* SQLAlchemy のように、2to3 使った対応は変態
* 最初に 2to3 を一回使うのはあり（おすすめ）
* Python2.7 と Python3.3 以外のサポートは捨てると楽


感想（C 拡張）
==============

* C 拡張があるものはやっぱり大変
* Python のヘッダーとソースを見て頑張ればなんとかなる
* 特に Python.h を読もう
* Python のソースでは Objects ディレクトリの下のコードを読むべし
* Python 2.7 と Python 3 の間では、マクロで両方で動かせるよう考慮されてる
* でも、module の初期化のコードだけは大きく違う

感想（狙い目について）
======================

* 多くの人が使っていて、かつコードのメンテナンスがあまりおこなわれてないもの
* pure python で動くもの
* Python2 で十分なテストがあるもの（もしくはテストを書く）


Python3 in PyCon JP 2012
=============================================

* Pythonを取り巻く開発環境
   http://2012.pycon.jp/program/sessions.html#session-16-1100-room357-ja
* Python 3でここまでできる Web プログラミング (by @aodag)
   http://2012.pycon.jp/program/sessions.html#session-16-1515-room433-ja
* Pyramid Sprint (by @aodag)
   https://github.com/Pylons/pyramid/wiki/Sprint-Ideas

ご清聴ありがとうございました
=============================

Happy Hacking
