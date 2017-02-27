---
title: "プロジェクトのモデリング | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト オブジェクトを実装するオートメーション [Visual Studio SDK]"
  - "プロジェクト モデルでは、オートメーション"
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# プロジェクトのモデリング
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトにオートメーションを提供する次の手順では標準プロジェクトのオブジェクトを実装することです : <xref:EnvDTE.Projects> のコレクションと `ProjectItems` ; `Project` のオブジェクトと <xref:EnvDTE.ProjectItem> ; および一意の実装へのそのほかのオブジェクト。  これらのオブジェクトは標準 Dteinternal.h ファイルで定義されます。  標準のオブジェクトの実装は BscPrj の例を示します。  モデルは他のプロジェクトからプロジェクトのオブジェクトと side\-by\-side する独自の標準プロジェクトのオブジェクトの作成にこれらのクラスを使用できます。  
  
 オートメーションのコンシューマーは n がソリューション内の特定のプロジェクトを取得するインデックス番号です。<xref:EnvDTE.Solution> ``  を呼び出すことができると仮定します \(「 `<UniqueProjName>")`  と <xref:EnvDTE.ProjectItems> \(`n`\)。  この自動化を呼び出すと環境は ItemID のパラメーターとして VSITEMID\_ROOT と VSHPROPID のパラメーターとして VSHPROPID\_ExtObject を渡す適切なプロジェクト階層で <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> を呼び出します。  `IVsHierarchy::GetProperty` は実装したコア `Project` インターフェイスを使用して `IDispatch` オートメーション オブジェクトへのポインターを返します。  
  
 次に `IVsHierarchy::GetProperty` 構文です。  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 プロジェクトは入れ子とプロジェクト項目のグループを作成するために使用するコレクションが格納されます。  階層の外観は次のようになります。  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 入れ子は `ProjectItems` のコレクションが入れ子になったオブジェクトを含むことができるので<xref:EnvDTE.ProjectItem> のオブジェクトが同時に <xref:EnvDTE.ProjectItems> のコレクションを指定できることを意味します。  基本的なプロジェクトでこの例では入れ子は表示されません。  `Project` のオブジェクトを実装することにより全体的なオートメーション モデルのデザイン機能を付けるような構造体の形式があります。  
  
 プロジェクト オートメーションは次の図のパスが表示されます。  
  
 ![Visual Studio プロジェクト オブジェクト](../../extensibility/internals/media/projectobjects.png "ProjectObjects")  
プロジェクト オートメーション  
  
 `Project` のオブジェクトを実装していない場合環境はプロジェクトの名前のみを含む `Project` の一般的なオブジェクトを返します。  
  
## 参照  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>