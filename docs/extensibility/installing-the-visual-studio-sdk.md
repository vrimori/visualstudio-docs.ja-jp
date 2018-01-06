---
title: "Visual Studio SDK をインストールする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: visual-studio-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 13ce2a839c09aa65c2bed2d87aec63827ec6583c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK をインストールします。
Visual Studio SDK は、Visual Studio セットアップで省略可能な機能です。 後でまた VS SDK をインストールすることができます。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio のインストールの一部として Visual Studio SDK をインストールします。  
 VSSDK を Visual Studio のインストールに含めるには、インストールしてください、 **Visual Studio 拡張機能開発**ワークロード**その他のツールセット**です。 これは、必要な前提条件と同様に、Visual Studio SDK にインストールされます。 選択して、インストールをさらにチューニングできます。 または、選択を解除するコンポーネントの概要を表示します。 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio のインストール後に Visual Studio SDK をインストールします。  
 Visual Studio のインストールを完了した後、Visual Studio SDK をインストールする場合は、Visual Studio インストーラーを再実行し、選択、 **Visual Studio 拡張機能開発**ワークロード。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>ソリューションから Visual Studio SDK をインストールします。  
 VSSDK を最初にインストールせず、拡張機能プロジェクトとソリューションを開く場合は、ソリューション エクスプ ローラーの上に強調表示された情報バーを求められます。 次のようになります。  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>コマンドラインから Visual Studio SDK をインストールします。  
任意の Visual Studio のワークロードやコンポーネントと同様に、コマンドラインから項目をインストールすることもできます。 参照してください[コマンド ライン パラメーターを使用して、Visual Studio のインストールを](../install/use-command-line-parameters-to-install-visual-studio.md)適切なコマンド ライン スイッチとワークロードまたはコンポーネントの識別子を確認する方法の詳細。
  
 Visual Studio のインストールされているバージョンに対応する Visual Studio インストーラーを使用する必要がありますに注意してください。 たとえば、コンピューターにインストールされている Visual Studio Enterprise がある場合は、Visual Studio Enterprise インストーラー (vs_enterprise.exe) を実行する必要があります。