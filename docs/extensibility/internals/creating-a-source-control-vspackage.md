---
title: "ソース コントロール VSPackage を作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理パッケージを作成するソース管理 [Visual Studio SDK]"
  - "ソース管理パッケージ"
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# ソース コントロール VSPackage を作成します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ここでは統合されたソース管理パッケージ アーキテクチャの概要に [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]実装されるインターフェイスおよび実行するサービスによって定義された単純なソース管理パッケージの実装を示すサンプルが含まれています\) を持つリンクを示します。  
  
 ソース管理 VSPackage を使用すると[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を使用すると統合するにはソース コントロールの内側の統合のパスを作成できます。  これは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] でバイパスしプロジェクトのソース管理システムからの要求にホストし既定のソース コントロールの UI を  **ソリューション エクスプローラー**  などの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のコンポーネントとやり取りするためのパッケージができます。  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] はサービスのモデルを使用して [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] と統合する VSPackage を作成する機能を持つ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のパートナーにアクセス許可を与えます。  
  
## このセクションの内容  
 [作業の開始](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のソース管理機能を実装するためのソース管理プラグインに高度な方法とソース管理パッケージについて説明します。  
  
 [アーキテクチャ](../../extensibility/internals/source-control-vspackage-architecture.md)  
 図を示しソース管理パッケージ コンポーネントについて説明します。  
  
 [フィーチャー](../../extensibility/internals/source-control-vspackage-features.md)  
 パッケージ ソース管理のさまざまな機能について説明します。  
  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 パッケージのソース管理統合するために実行する必要のある VSPackage の構造体について説明します。  
  
## 関連項目  
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のソース管理のユーザー インターフェイスのソース管理プラグインをそのためのソース管理機能作成する方法について \(UI\) 説明します。  
  
 [ソース管理](../../extensibility/internals/source-control.md)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の統合機能としてソース管理を実装するためのオプションについて説明します。