---
title: "モデリング プロジェクト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d654669ad35ce77d840f4852ceb7a6605a8221be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="project-modeling"></a>プロジェクトのモデリング
プロジェクトは、標準プロジェクト オブジェクトを実装するために、オートメーションを提供することで、次の手順:<xref:EnvDTE.Projects>と`ProjectItems`コレクション以外の場合は、`Project`と<xref:EnvDTE.ProjectItem>オブジェクトと、実装に固有の残りのオブジェクト。 これらの標準的なオブジェクトは、Dteinternal.h ファイルで定義されます。 BscPrj サンプルでは、標準的なオブジェクトの実装を提供します。 サイド バイ サイドを強調する、独自の標準的なプロジェクト オブジェクトを作成するモデルとしてこれらのクラスを使用するその他のプロジェクトの種類のプロジェクトのオブジェクトとします。  
  
 オートメーション コンシューマーが呼び出すことができる前提<xref:EnvDTE.Solution>("`<UniqueProjName>")`と<xref:EnvDTE.ProjectItems>(`n`) ここで n は、ソリューション内の特定のプロジェクトを取得するため、インデックス番号します。 呼び出して環境このオートメーション呼び出しを行うと、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> ItemID パラメーターと VSHPROPID パラメーターとして VSHPROPID_ExtObject に VSITEMID_ROOT を渡すこと、適切なプロジェクトの階層にします。 `IVsHierarchy::GetProperty`返します、`IDispatch`コアを提供するオートメーション オブジェクトへのポインター`Project`インターフェイスを実装しています。  
  
 構文は、次の`IVsHierarchy::GetProperty`します。  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 プロジェクトでは、入れ子に対応して、プロジェクト項目のグループを作成するコレクションを使用します。 次のような階層が表示されます。  
  
```  
Projects  
  |- Project  
      |- ProjectItems (a collection of ProjectItem)  
          |- ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 入れ子ことを意味、<xref:EnvDTE.ProjectItem>オブジェクトには<xref:EnvDTE.ProjectItems>同時コレクションのため、`ProjectItems`コレクションは、入れ子になったオブジェクトを含めることができます。 基本的なプロジェクト サンプルには、この入れ子は示しません。 実装することによって、`Project`オブジェクトの全体的なオートメーション モデルのデザインの特徴を表すツリー状の構造に参加します。  
  
 プロジェクトの自動化は、次の図でパスをたどります。  
  
 ![Visual Studio プロジェクト オブジェクト](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
プロジェクトの自動化  
  
 実装しない場合、`Project`オブジェクト、環境はジェネリック型を返しますまだ`Project`プロジェクトの名前のみを含むオブジェクトです。  
  
## <a name="see-also"></a>関連項目  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>