---
title: "VSPackage 構造 (ソース コントロールの vs パッケージ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vspackages にある、構造体"
  - "ソース管理パッケージ、VSPackage の概要"
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# VSPackage 構造 (ソース コントロールの vs パッケージ)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソース コントロール パッケージ SDK VSPackage を作成するためのガイドラインにより、ソースのコントロール実装側で自分のソース管理機能を統合するには、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 環境です。 VSPackage が COM コンポーネントからの要求時に読み込まれた通常、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) が、レジストリ エントリのパッケージによって提供されているサービスに基づいています。 すべての VSPackage を実装する必要があります、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>です。 VSPackage が通常によって提供されるサービスを利用する、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE proffers 独自の一部のサービスとします。  
  
 VSPackage では、そのメニュー項目を宣言し、.vsct ファイルを使用して既定の項目の状態を確立します。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE では、VSPackage が読み込まれるまでこの状態でメニュー項目を表示します。 その後は、VSPackage の実装、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> を有効にする、またはメニュー項目を無効にするメソッドが呼び出されます。  
  
## ソース コントロールのパッケージ特性  
 VSPackage が密接に統合されたソース管理 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
 VSPackage のセマンティクスは次のとおりです。  
  
-   ある VSPackage ことによって実装されるインターフェイス \(、 `IVsPackage` インターフェイス\)  
  
-   UI コマンドの実装 \(.vsct ファイルとの実装、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイス\)  
  
-   VSPackage での登録 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
 ソース管理 VSPackage と通信しなければならないこれら他の [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] エンティティ。  
  
-   プロジェクト  
  
-   エディター  
  
-   ソリューション  
  
-   Windows  
  
-   実行中のドキュメント テーブル  
  
### Visual Studio 環境のサービス利用できる場合があります。  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider サービス  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### VSIP インターフェイスを実装およびと呼ばれる  
 ソース管理パッケージは、VSPackage とために登録されているその他の VSPackages に直接対話できます [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 広範なソース管理機能を提供するためにソース管理 VSPackage に対処できるプロジェクトまたはシェルによって提供されるインターフェイスです。  
  
 すべてのプロジェクトに [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を実装する必要があります、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> 内のプロジェクトとして認識されるように、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。 ただし、このインターフェイスに特化されていないソース管理は十分です。 ソースの下にあると予想されるプロジェクト管理の実装、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>です。 その内容にプロジェクトを照会し、グリフとバインディング情報 \(サーバーの場所とソース管理下にあるプロジェクトのディスク上の場所間の接続を確立するために必要な情報\) を提供するソース管理の VSPackage によってこのインターフェイスが使用されます。  
  
 VSPackage を実装するソース管理、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, 、それによってプロジェクトをソース管理のために登録して、そのステータス グリフを取得します。  
  
 ソース管理 VSPackage が考慮する必要があるインターフェイスの一覧については、次を参照してください。 [関連するサービスとインターフェイス](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)します。  
  
## 参照  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [関連するサービスとインターフェイス](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)