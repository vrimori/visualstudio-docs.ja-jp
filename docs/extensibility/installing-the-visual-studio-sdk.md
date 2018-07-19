---
title: Visual Studio SDK のインストール |Microsoft Docs
ms.custom: ''
ms.date: 07/12/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fc2d0accfdae3587d43727ec1e0eda0785510c85
ms.sourcegitcommit: 0853338831925fc63398b49f21f457b39f3c0a12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/13/2018
ms.locfileid: "39030430"
---
# <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK をインストールします。

Visual Studio SDK (ソフトウェア開発キット) は、Visual Studio セットアップで省略可能な機能です。 また、後から VS SDK をインストールすることもできます。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio のインストールの一部として、Visual Studio SDK をインストールします。

VS SDK を Visual Studio のインストールに含めるには、インストール、 **Visual Studio 拡張機能の開発**ワークロード下で**その他のツールセット**します。 このワークロードは、Visual Studio SDK と必要な前提条件にインストールされます。 オンまたはオフからコンポーネントによって、インストールをさらにチューニングできます、**概要**ビュー。
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio をインストールした後、Visual Studio SDK をインストールします。

Visual Studio のインストールが完了した後、Visual Studio SDK をインストールするに、Visual Studio インストーラーを再実行し、選択、 **Visual Studio 拡張機能の開発**ワークロード。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>ソリューションから Visual Studio SDK をインストールします。

最初に、VS SDK をインストールしなくても、拡張機能プロジェクトとソリューションを開く場合求められますが、**不足している機能のインストール**をインストールするためのダイアログ、 **Visual Studio 拡張機能の開発**ワークロードの場合:

![拡張機能の開発をインストール](../extensibility/media/install-extension-development.png "拡張機能の開発のインストール")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>コマンドラインから Visual Studio SDK をインストールします。

ように、Visual Studio のワークロードやコンポーネントをインストールすることも、 **Visual Studio 拡張機能の開発**ワークロード (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) コマンドラインから。 参照してください[コマンド ライン パラメーターを使用して、Visual Studio をインストールする](../install/use-command-line-parameters-to-install-visual-studio.md)適切なコマンド ライン スイッチとワークロードまたはコンポーネントの識別子を特定する方法について一般的な手順の詳細について。
  
Visual Studio のインストールされているバージョンに一致する Visual Studio インストーラーを使用する必要がありますに注意してください。 たとえば、Visual Studio Enterprise がコンピューターにインストールした場合は、Visual Studio Enterprise インストーラー (vs_enterprise.exe) を実行する必要があります。