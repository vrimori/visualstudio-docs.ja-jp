---
title: "Visual Studio 拡張機能を配布 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf74110cf42daa51521cc7ea706c1b951b23deb8
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="shipping-visual-studio-extensions"></a>Visual Studio 拡張機能の配布
拡張機能開発が終了したら後、は、他のコンピューターにインストールして、友人や同僚と共有または Visual Studio Marketplace に発行できます。 このセクションの内容を発行して、拡張機能を維持するために行うには必要なすべての情報を用いて: 発行、更新して、ローカライズ、.vsix ファイルを操作します。  
  
## <a name="working-with-vsix-extensions"></a>VSIX 拡張機能の使用  
 VSIX 拡張機能は、空の VSIX プロジェクトを作成し、別のアイテム テンプレートにして作成できます。 詳細については、次を参照してください。 [VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)です。  
  
 できる形式を使用して、VSIX パッケージ プロジェクト テンプレート、項目テンプレート、Vspackage、Managed Extensibility Framework (MEF) コンポーネント、**ツールボックス**コントロール、アセンブリ、およびカスタム型 (カスタム スタート ページを含む)。 VSIX 形式では、ファイル ベースの展開を使用します。 VSIX パッケージの詳細については、次を参照してください。 [VSIX パッケージの構造は](../extensibility/anatomy-of-a-vsix-package.md)します。  
  
 VSIX 形式は、コード スニペットのインストールをサポートしていません。 できませんグローバル アセンブリ キャッシュ (GAC) にまたはシステム レジストリへの書き込みなどの他の特定のシナリオ。 GAC またはインストールのレジストリに書き込む必要がある場合は、Windows インストーラーを使用する必要があります。 詳細については、次を参照してください。[を準備する拡張機能の Windows インストーラーの配置](../extensibility/preparing-extensions-for-windows-installer-deployment.md)です。  
  
## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>拡張機能を Visual Studio Marketplace に発行  
 メーリングに .vsix ファイルまたはサーバー上に配置することだけで他の人に、拡張機能を配布することができます。 多くの人の手でコードを取得する最善の方法が、 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)です。 Visual Studio Marketplace 拡張機能のユーザーが使用できる Visual Studio を通じて**拡張機能と更新プログラム**です。 詳細については、「[Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)」を参照してください。  
  
 Visual Studio Marketplace に拡張機能をアップロードする方法を示す完全な例を参照してください。[チュートリアル: Visual Studio 拡張機能を公開](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)です。  
  
## <a name="private-galleries"></a>Private Galleries  
 コントロール、テンプレート、およびツールを開発するときは、イントラネットのプライベート ギャラリーに送信することによって、組織と共有してできます。 詳細については、「[プライベート ギャラリー](../extensibility/private-galleries.md)」を参照してください。  
  
## <a name="localizing-your-extension"></a>拡張機能のローカライズ  
 を別のロケールで拡張機能をリリースする予定している場合は、ローカライズすることを検討してください。 含まれている新機能の詳細については、次を参照してください。 [VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)です。  
  
## <a name="updating-and-versioning-your-extension"></a>更新およびバージョン管理、拡張機能  
 拡張機能を公開した後に更新する必要がある場合に取得します。 Visual Studio Marketplace で公開されている拡張機能を更新する方法を調べるには、次を参照してください。[する方法: 拡張機能を更新](../extensibility/how-to-update-a-visual-studio-extension.md)です。  
  
 Visual Studio の複数のバージョンをサポートするために、拡張機能を設定することができます。 詳細については、次を参照してください。[をサポートする複数のバージョンの Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)です。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[VSIX プロジェクトのテンプレートの概要](../extensibility/getting-started-with-the-vsix-project-template.md)|VSIX プロジェクト テンプレートを使用してカスタム プロジェクト テンプレートをインストールする方法について説明します。|  
|[VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)|VSIX パッケージのコンポーネントについて説明します。|  
|[VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)|手順をパッケージ化し、拡張機能を公開する方法について説明します。|  
|[VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)|Extension.vsixlangpack ファイルを使用して、インストール プロセスのローカライズされたテキストを提供する方法について説明します。|  
|[方法: 拡張機能を更新](../extensibility/how-to-update-a-visual-studio-extension.md)|既存の Visual Studio 拡張機能の更新プログラムを展開する方法と、システム上の拡張機能を更新する方法について説明します。|  
|[方法: VSIX パッケージへの依存関係の追加](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|VSIX 展開パッケージへの参照を追加する方法について説明します。|  
|[Windows インストーラーの配置に関する拡張機能を準備する](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Windows インストーラーで拡張機能を配置する方法について説明します。|  
|[VSIX パッケージの署名](../extensibility/signing-vsix-packages.md)|VSIX パッケージに署名する方法をについて説明します。|  
|[プライベート ギャラリー](../extensibility/private-galleries.md)|拡張機能のプライベート ギャラリーを作成する方法について説明します。|  
|[複数バージョンの Visual Studio をサポートする](../extensibility/supporting-multiple-versions-of-visual-studio.md)|複数のバージョンの Visual Studio の拡張機能をサポートする方法を示します。|
|[Visual Studio の検索](locating-visual-studio.md)|カスタム拡張機能の展開用の Visual Studio インスタンスを検索する方法について説明します。|
