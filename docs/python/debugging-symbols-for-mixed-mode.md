---
title: "Python Tools for Visual Studio の混合モードのデバッグ用のシンボル | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be5fdf2f-b55f-488a-9772-58adfe07a7ab
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 9f7ba91262875344ded1e09277883abff292f359
ms.lasthandoff: 03/07/2017

---

# <a name="installing-debugging-symbols-for-python-interpreters"></a>Python インタープリターのデバッグ シンボルのインストール

完全なデバッグ エクスペリエンスを提供するため、Python Tools for Visual Studio (PTVS) の[混合モードのデバッグ](debugging-mixed-mode.md)では、使用する Python インタープリター内の多数の内部データ構造を解析する必要があります。 これには、インタープリター自体のデバッグ シンボルが必要です。 たとえば、python27.dll に対応するシンボル ファイルは python27.pdb です。

PTVS は、シンボルが必要であることを検出すると、シンボル ファイルを含むフォルダーを指示するかファイルのダウンロードを求めるメッセージを表示します。

![混合モードのデバッグ時のシンボルのプロンプト](media/mixed-mode-debugging-symbols-required.png) 

シンボル ファイルは、この後の説明に従って、[公式ディストリビューション](#official-distribution)または [Enthought Canopy](#enthought-canopy) からダウンロードすることができます。 ActiveState Python などのサードパーティの Python ディストリビューションを使用している場合は、そのディストリビューションの作成者に連絡して、シンボルの提供を依頼する必要があります  (ただし、WinPython には、標準の Python インタープリターが変更なしで組み込まれているため、対応するバージョン番号用の公式ディストリビューションのシンボルを使用できます)。

インタープリターの .pdb ファイルを入手したら、次の手順に従って PTVS がそれらを認識するように設定して、デバッグ セッションの開始時に自動的に読み込まれるようにします。

1. **[ツール] メニューの [オプション]** コマンドを選択し、**[デバッグ]、[シンボル]** の順に選択します。

![混合モードのデバッグでのシンボルのオプション](media/mixed-mode-debugging-symbols.png)

1. ツールバーの [追加] ボタン (上の図で [!] アイコンの右隣、複数のボタンの左端にあるボタン) を選択し、.pdb を格納するフォルダーに移動し、**[OK]** をクリックします。


## <a name="official-distribution"></a>公式ディストリビューション

Python 3.5 以降では、インストーラーを使用してデバッグ シンボルを含めることができます。(新しくインストールするか、既存のインストールを変更します)。 **[Custom installation (カスタム インストール)]** を選択し、**[Next (次へ)]** を選択します。**[Advanced Options (高度なオプション)]** 画面で、[Download debugging symbols (デバッグ シンボルのダウンロード)]**と**[Download debug binaries** (デバッグ バイナリのダウンロード)] を選択します。

![デバッグ シンボルを含む Python 3.x インストーラー](media/mixed-mode-debugging-symbols-installer35.png)

Python 3.4.x 以前では、シンボルはダウンロード可能な .zip ファイルとして入手できます。 ファイルをダウンロードしてフォルダーに抽出した後、前のセクションの指示に従って、それらを PTVS に登録してください。

| Python のバージョン | ダウンロード | 
| --- | --- | 
| 3.4.4 | [32 ビット](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64 ビット](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 ビット](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64 ビット](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 ビット](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64 ビット](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 ビット](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64 ビット](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 ビット](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64 ビット](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 ビット](http://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64 ビット](http://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 ビット](http://python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64 ビット](http://python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 ビット](http://python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64 ビット](http://python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 ビット](http://python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64 ビット](http://python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 ビット](http://python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64 ビット](http://python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 ビット](http://python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64 ビット](http://python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.11 | [32 ビット](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64 ビット](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 ビット](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64 ビット](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 ビット](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64 ビット](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 ビット](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64 ビット](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 ビット](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64 ビット](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 ビット](http://python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64 ビット](http://python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 ビット](http://python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64 ビット](http://python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 ビット](http://python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64 ビット](http://python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 ビット](http://python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64 ビット](http://python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 ビット](http://python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64 ビット](http://python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 ビット](http://python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64 ビット](http://python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |


## <a name="enthought-canopy"></a>Enthought Canopy

Enthought Canopy は、バージョン 1.2 以降、バイナリのシンボルを提供します。 それらはディストリビューションと共に自動的にインストールされますが、それらが格納されたフォルダーをシンボル パスに追加する操作は手動で実行する必要があります。 Canopy の一般的なユーザーごとのインストールでは、シンボルは、64 ビット版では `%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts`に、32 ビット版では `%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts` に配置されます。

Enthought Canopy 1.1 以前と Enthought Python Distribution (EPD) はインタープリター シンボルの提供がないため、混合モードのデバッグには対応できません。
