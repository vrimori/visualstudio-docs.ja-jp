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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 722c32c139d2f560fa6d10aba9fd8bac610f9f20
ms.lasthandoff: 03/07/2017

---
# <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK をインストールします。
Visual Studio SDK は、Visual Studio のセットアップで省略可能な機能です。 後で、VS SDK をインストールすることもできます。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio のインストールの一部として Visual Studio SDK をインストールします。  
 インストールする必要があります、VSSDK を Visual Studio のインストールに含める場合は、 **Visual Studio 拡張機能の開発**ワークロード**その他のツールセット**します。 これは、必要な前提条件と同様に、Visual Studio SDK にインストールされます。 選択して、インストールをさらにチューニングできますし、選択を解除するコンポーネントの概要を表示したりできます。 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio のインストール後、Visual Studio SDK をインストールします。  
 Visual Studio のインストールが完了した後、Visual Studio SDK をインストールする場合は、Visual Studio インストーラーを再実行し、選択、 **Visual Studio 拡張機能の開発**ワークロード。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>ソリューションから Visual Studio SDK をインストールします。  
 最初に、VSSDK をインストールすることがなく、拡張機能プロジェクトとソリューションを開く場合は、ソリューション エクスプ ローラーの上の強調表示された情報バーに促されます。 次のようになります。  
  
 ![SolutionExplorerInstall](~/extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>コマンドラインから Visual Studio SDK をインストールします。  
任意の Visual Studio のワークロードやコンポーネントと同様に、コマンドラインから項目をインストールすることもできます。 参照してください[コマンド ライン パラメーターを使用して、Visual Studio のインストールを](../install/use-command-line-parameters-to-install-visual-studio.md)適切なコマンド ライン スイッチとワークロードまたはコンポーネントの識別子を確認する方法の詳細。
  
 Visual Studio のインストールされているバージョンに対応する Visual Studio インストーラーを使用する必要があることに注意してください。 たとえば、お使いのコンピューターにインストールされている Visual Studio Enterprise がある場合は、Visual Studio Enterprise インストーラー (vs_enterprise.exe) を実行する必要があります。
