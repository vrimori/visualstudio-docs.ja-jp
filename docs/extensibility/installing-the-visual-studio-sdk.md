---
title: Visual Studio SDK をインストールする |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 259646e0dbee4831db83a7098954d1c5144d8ead
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK をインストールします。
Visual Studio SDK は、Visual Studio セットアップで省略可能な機能です。 また、後から VS SDK をインストールすることもできます。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio のインストールの一部として Visual Studio SDK をインストールします。  
 VSSDK を Visual Studio のインストールに含めるには、インストールしてください、 **Visual Studio 拡張機能開発**ワークロード**その他のツールセット**です。 これは、必要な前提条件と同様に、Visual Studio SDK にインストールされます。 選択して、インストールをさらにチューニングできます。 または、選択を解除するコンポーネントの概要を表示します。 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio のインストール後に Visual Studio SDK をインストールします。  
 Visual Studio のインストールを完了した後、Visual Studio SDK をインストールする場合は、Visual Studio インストーラーを再実行し、選択、 **Visual Studio 拡張機能開発**ワークロード。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>ソリューションから Visual Studio SDK をインストールします。  
 VSSDK を最初にインストールせず、拡張機能プロジェクトとソリューションを開く場合は、ソリューション エクスプ ローラーの上に強調表示された情報バーを求められます。 次のようになります。  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>コマンドラインから Visual Studio SDK をインストールします。  
ように、Visual Studio ワークロードまたはコンポーネントをインストールすることも、 **Visual Studio 拡張機能開発**ワークロード (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) コマンドラインからです。 参照してください[コマンド ライン パラメーターを使用して、Visual Studio のインストールを](../install/use-command-line-parameters-to-install-visual-studio.md)詳細については、適切なコマンド ライン スイッチ、およびワークロードまたはコンポーネントの識別子を特定する方法についての一般的な手順です。
  
 Visual Studio のインストールされているバージョンに対応する Visual Studio インストーラーを使用する必要がありますに注意してください。 たとえば、コンピューターにインストールされている Visual Studio Enterprise がある場合は、Visual Studio Enterprise インストーラー (vs_enterprise.exe) を実行する必要があります。