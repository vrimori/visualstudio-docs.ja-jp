---
title: "Visual Studio 拡張機能を配布 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX 配置"
  - "VSIX の展開"
  - "VSIX パッケージでは、サテライト Dll"
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Visual Studio 拡張機能を配布
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

拡張機能の開発が完了したら後、は、他のコンピューターにインストールして、友人や同僚と共有または Visual Studio ギャラリーに発行できます。 このセクションで発行し、拡張機能を維持するために行う必要のあるすべての事項について説明します。 .vsix ファイル、公開、ローカライズ、および更新を操作します。  
  
## VSIX 拡張機能の使用  
 空の VSIX プロジェクトを作成して、別の項目テンプレートを追加して、VSIX 拡張機能を作成できます。 詳細については、「[VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)」を参照してください。  
  
 プロジェクト テンプレートをパッケージ化、テンプレート、vspackages にある、Managed Extensibility Framework \(MEF\) コンポーネントの項目を VSIX 形式を使用する **ツールボックス** コントロール、アセンブリ、およびカスタムの型 \(カスタム スタート ページを含む\)。 VSIX 形式では、ファイル ベースの展開を使用します。 VSIX パッケージの詳細については、次を参照してください。 [VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)します。  
  
 VSIX 形式は、コード スニペットのインストールをサポートしていません。 グローバル アセンブリ キャッシュ \(GAC\) またはシステムのレジストリへの書き込みなどの他の特定のシナリオもサポートされません。 GAC またはインストールのレジストリに書き込む必要がある場合は、Windows インストーラーを使用する必要があります。 詳細については、「[Windows インストーラーの配置の拡張機能を準備します。](../extensibility/preparing-extensions-for-windows-installer-deployment.md)」を参照してください。  
  
## 拡張機能を Visual Studio ギャラリーに発行します。  
 .Vsix ファイル \(郵送先\) に、サーバー上に変更したりするだけで他のユーザーに、拡張機能を配布することができます。 多くの人の手にコードを取得する最適な方法に配置する、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847)します。 Visual Studio ギャラリーの拡張機能は Visual Studio ユーザー **拡張機能と更新プログラム**します。 詳細については、「[Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)」を参照してください。  
  
 拡張機能を Visual Studio ギャラリーにアップロードする方法を示す完全な例を参照してください。 [チュートリアル: Visual Studio 拡張機能を公開します。](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)します。  
  
## プライベート ギャラリー  
 コントロール、テンプレート、およびツールを開発するときは、イントラネット上のプライベート ギャラリーに投稿することで、組織と共有することができます。 詳細については、「[プライベート ギャラリー](../extensibility/private-galleries.md)」を参照してください。  
  
## 拡張機能のローカライズ  
 別のロケールで拡張機能をリリースする場合は、ローカライズすることを検討してください。 に関する詳細については、次を参照してください。 [VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)します。  
  
## 更新と拡張機能のバージョン管理  
 拡張機能を公開した後に更新する必要がある場合に取得します。 Visual Studio ギャラリーにパブリッシュされている拡張機能を更新する方法については、次を参照してください。 [方法: 拡張機能を更新](../extensibility/how-to-update-a-visual-studio-extension.md)します。  
  
 Visual Studio の複数のバージョンをサポートするために、拡張機能を設定することができます。 詳細については、「[Visual Studio の複数のバージョンをサポートします。](../extensibility/supporting-multiple-versions-of-visual-studio.md)」を参照してください。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[VSIX プロジェクトのテンプレートの概要](../extensibility/getting-started-with-the-vsix-project-template.md)|VSIX プロジェクトのテンプレートを使用してカスタム プロジェクト テンプレートをインストールする方法について説明します。|  
|[VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)|VSIX パッケージのコンポーネントについて説明します。|  
|[VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)|手順をパッケージ化し、拡張機能を公開する方法について説明します。|  
|[VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)|Extension.vsixlangpack ファイルを使用して、インストール プロセスのローカライズされたテキストを提供する方法について説明します。|  
|[方法: 拡張機能を更新](../extensibility/how-to-update-a-visual-studio-extension.md)|既存の Visual Studio 拡張機能に更新を展開する方法と、システム上の拡張機能を更新する方法について説明します。|  
|[方法: VSIX パッケージへの依存関係の追加](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|展開の VSIX パッケージへの参照を追加する方法について説明します。|  
|[Windows インストーラーの配置の拡張機能を準備します。](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Windows インストーラーで、拡張機能を展開する方法について説明します。|  
|[VSIX パッケージに署名します。](../extensibility/signing-vsix-packages.md)|VSIX パッケージに署名する方法をについて説明します。|  
|[プライベート ギャラリー](../extensibility/private-galleries.md)|拡張機能のプライベート ギャラリーを作成する方法について説明します。|  
|[Visual Studio の複数のバージョンをサポートします。](../extensibility/supporting-multiple-versions-of-visual-studio.md)|複数のバージョンの Visual Studio の拡張機能をサポートする方法を示します。|