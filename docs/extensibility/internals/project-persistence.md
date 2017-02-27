---
title: "プロジェクトの永続化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクトの永続性"
  - "プロジェクト [Visual Studio SDK] の永続化"
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# プロジェクトの永続化
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

永続性はプロジェクトの主要な設計です。  ファイルを表すほとんどのプロジェクトで使用できるプロジェクト項目 ; データはファイル ベースであるか [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトのサポート。  プロジェクトとプロジェクト ファイルが所有しているファイルも保持する必要があります。  IDE では自身またはプロジェクト項目を格納する Project に指示します。  
  
 プロジェクトのテンプレートはプロジェクト ファクトリに渡されます。  テンプレートには特定の種類のプロジェクトの要件に従ってすべてのプロジェクト項目の初期化をサポートする必要があります。  これらのテンプレートはソリューションを使用してIDE でプロジェクト ファイルとマネージ コードとして後で保存できます。  詳細については、「[プロジェクトのファクトリを使用して、プロジェクトのインスタンスを作成します。](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)」および「[ソリューション](../../extensibility/internals/solutions.md)」を参照してください。  
  
 プロジェクト項目はファイル ベースまたは非ファイル ベースです :  
  
-   ファイル ベースの項目はローカルまたはリモートになります。  リモート システムの C\# Web プロジェクトではファイルへの接続はファイル自体がリモート システムで保持されるのに対しローカルで保持されます。  
  
-   非ファイル ベースの項目はデータベースまたはリポジトリに保存できます。  
  
## コミット モデル  
 プロジェクト項目の場所を決定したら適切なコミット モデルを選択する必要があります。  たとえばローカル ファイルを使用してファイル ベース モデルでは各プロジェクトは独立した的に保存できます。  リポジトリ モデルでは1 回のトランザクションの複数の項目を格納できます。  詳細については、「[プロジェクトの種類のデザインの決定](../../extensibility/internals/project-type-design-decisions.md)」を参照してください。  
  
 ファイル名拡張子を確認するにはプロジェクトにはボックスに情報を提供する ENT4ENT \[入力\] ドロップダウン リストを表示して最初のファイル名拡張子を管理するように <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> のインターフェイスを ENT3ENT \[入力\] ダイアログの実装するオブジェクトのクライアントが有効になり実行します。  
  
 IDE でプロジェクトが適切に永続化する必要があることを示すプロジェクト項目の `IPersistFileFormat` プロジェクトのインターフェイスを呼び出します。  したがってオブジェクトはファイルとファイル形式のあらゆる面を所有します。  これはオブジェクト ファイル形式の名前が含まれています。  
  
 項目がファイルの場合`IPersistFileFormat` は非ファイル ベースの項目を保持する方法です。  [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] プロジェクトの [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] のプロジェクトまたは .vcproj ファイルの .vbp ファイルなどプロジェクト ファイルは保持する必要があります。  
  
 保存操作のために連続したドキュメントのテーブルを調べて\(RDT\) 階層は <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> のインターフェイスに渡します。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> のメソッドは項目が変更されているかどうかを判断するために実行されます。  項目がない場合変更された項目を保存するには<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> のメソッドが実行されます。  
  
 `IVsPersistHierarchyItem2` インターフェイスのメソッドを再度読み込むに項目が項目がある場合は再度読み込むことができるかどうかを確認するために使用されます。  また<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> のメソッドが変更された項目を保存せずに破棄実行できます。  
  
## 参照  
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [プロジェクトのファクトリを使用して、プロジェクトのインスタンスを作成します。](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)