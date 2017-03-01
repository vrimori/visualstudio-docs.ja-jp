---
title: "Visual Studio SDK をインストールする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 9c25532605613b34ded15a4bd6a533e589b7fce2
ms.openlocfilehash: d039c50cea2ee038baec26fad02a98ae45f0d521
ms.lasthandoff: 02/22/2017

---
# <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK をインストールします。
Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio のインストールの一部として Visual Studio SDK をインストールします。  
 Visual Studio のインストールに、VSSDK を含める場合は、カスタム インストールを行う必要があります。  
  
> [!NOTE]
>  実行可能ファイルのインストールで、Visual Studio SDK と呼ばれる**Visual Studio Extensibility Tools**します。  
  
1.  Visual Studio 2015 のインストールを開始します。 Visual Studio Express 以外の任意のエディションをインストールすることができます。  
  
2.  最初の画面では、次のように選択します。**カスタム**ではなく、**既定**します。 **[次へ]**をクリックします。  
  
3.  カスタムの機能のツリー ビューが表示されます。 開いている**一般的なツール**します。 はず**Visual Studio Extensibility Tools**します。  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  確認**Visual Studio Extensibility Tools** 、順にクリックして**次**してインストールを続行します。  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio のインストール後、Visual Studio SDK をインストールします。  
 Visual Studio のインストールが完了した後、Visual Studio SDK をインストールする場合は、次の手順に従います必要があります。  
  
1.  移動して**コントロール パネル]、[プログラム]、[プログラムし、機能**を探します**Visual Studio 2015**します。 Express 以外の Visual Studio 2015 の任意のエディションの Visual Studio SDK をインストールすることができます。  
  
2.  右クリック**Visual Studio 2015**、クリックして**変更**します。 [インストール] ページが表示されます。  
  
3.  同じ手順に従って**Visual Studio のインストールの一部として、Visual Studio SDK をインストールする**上です。  
  
4.  クリックして、 **Visual Studio Extensibility Tools**を Visual Studio SDK をインストールするリンク。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>ソリューションから Visual Studio SDK をインストールします。  
 最初に、VSSDK をインストールすることがなく、拡張機能プロジェクトとソリューションを開く場合は、ソリューション エクスプ ローラーの上の強調表示された情報バーに促されます。 次のようになります。  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>コマンドラインから Visual Studio SDK をインストールします。  
 使用してコマンドラインから、VSSDK をインストールすることができます、 **/InstallSelectableItems** Visual Studio インストーラーに切り替えます。 インストーラーでのコマンド ライン パラメーターを使用する方法の詳細については、「[コマンド ライン パラメーターを使用して、Visual Studio インストールを](../install/use-command-line-parameters-to-install-visual-studio.md)します。  
  
 何も行わずにインストーラーを使用して、Visual Studio 2015 Community VSSDK をインストールする方法を次に示します。  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Visual Studio のインストールされているバージョンに対応する Visual Studio インストーラーを使用する必要があることに注意してください。 たとえば、お使いのコンピューターにインストールされている Visual Studio Enterprise がある場合は、Visual Studio Enterprise インストーラー (vs_enterprise.exe) を実行する必要があります。
