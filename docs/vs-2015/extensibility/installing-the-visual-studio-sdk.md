---
title: Visual Studio SDK のインストール |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1bbf029fb27e54b68fe6bef36d0c3f2f7329c45b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540072"
---
# <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK をインストールします。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio のインストールの一部として Visual Studio SDK をインストールします。  
 Visual Studio のインストールに VSSDK を含める場合は、カスタム インストールを実行する必要があります。  
  
> [!NOTE]
>  実行可能ファイルのインストールで、Visual Studio SDK と呼びます**Visual Studio Extensibility Tools**します。  
  
1.  Visual Studio 2015 のインストールを開始します。 Visual Studio Express 以外の任意のエディションをインストールすることができます。  
  
2.  最初の画面では、次のように選択します。**カスタム**ではなく、**既定**します。 **[次へ]** をクリックします。  
  
3.  カスタムの機能のツリー ビューが表示されます。 開いている**一般的なツール**します。 表示する必要があります**Visual Studio Extensibility Tools**します。  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  確認**Visual Studio Extensibility Tools** 、順にクリックします **[次へ]** インストールを続行します。  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio をインストールした後、Visual Studio SDK をインストールします。  
 Visual Studio のインストールが完了した後、Visual Studio SDK をインストールする場合は、次の手順を実行する必要があります。  
  
1.  移動して**コントロール パネル]、[プログラム]、[プログラムし、機能**、探して**Visual Studio 2015**します。 Express を除く Visual Studio 2015 の任意のエディションの Visual Studio SDK をインストールすることができます。  
  
2.  右クリックして**Visual Studio 2015**、 をクリックし、**変更**します。 [インストール] ページが表示されます。  
  
3.  同じ手順に従って**Visual Studio のインストールの一部として、Visual Studio SDK をインストールする**上。  
  
4.  をクリックして、 **Visual Studio Extensibility Tools** Visual Studio SDK のインストールへのリンク。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>ソリューションから Visual Studio SDK をインストールします。  
 VSSDK を最初にインストールしなくても、拡張機能プロジェクトとソリューションを開く場合は、ソリューション エクスプ ローラーの上の強調表示された情報バーにより促されます。 次のようになります。  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>コマンドラインから Visual Studio SDK をインストールします。  
 使用して、コマンドラインから VSSDK をインストールすることができます、 **/InstallSelectableItems** Visual Studio インストーラーに切り替えます。 インストーラーでのコマンド ライン パラメーターの使用に関する詳細については、次を参照してください。 [Visual Studio 2015 をインストールする](../install/install-visual-studio-2015.md)します。  
  
 Visual Studio 2015 Community インストーラーをサイレント モードで使用する VSSDK のインストール方法を次に示します。  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Visual Studio のインストールされているバージョンに一致する Visual Studio インストーラーを使用する必要がありますに注意してください。 たとえば、Visual Studio Enterprise がコンピューターにインストールした場合は、Visual Studio Enterprise インストーラー (vs_enterprise.exe) を実行する必要があります。







