---
title: プロジェクトのモデリング |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37b237a462900735ea641407d10719d43334262e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808415"
---
# <a name="project-modeling"></a>プロジェクトのモデリング
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プロジェクトは、標準的なプロジェクト オブジェクトを実装するは、オートメーションを提供するために、次の手順:<xref:EnvDTE.Projects>と`ProjectItems`コレクション、`Project`と<xref:EnvDTE.ProjectItem>オブジェクトと、実装に固有の残りのオブジェクト。 これらの標準的なオブジェクトは、Dteinternal.h ファイルで定義されます。 BscPrj サンプルでは、標準のオブジェクトの実装が提供されます。 サイド バイ サイドを強調する、独自の標準的なプロジェクト オブジェクトを作成するモデルとしてこれらのクラスを使用するその他のプロジェクトの種類のプロジェクトのオブジェクトとします。  
  
 呼び出せるように、automation のコンシューマーが前提としています<xref:EnvDTE.Solution>("`<UniqueProjName>")`と<xref:EnvDTE.ProjectItems>(`n`) n は、ソリューションで特定のプロジェクトを取得するため、インデックス番号。 環境を呼び出すこの automation 呼び出しを行うと、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> VSITEMID_ROOT を VSHPROPID_ExtObject VSHPROPID パラメーターとして、ItemID のパラメーターとして渡すこと、適切なプロジェクトの階層にします。 `IVsHierarchy::GetProperty` 返します、`IDispatch`コアを提供するオートメーション オブジェクトへのポインター`Project`インターフェイスを実装しています。  
  
 構文は、次の`IVsHierarchy::GetProperty`します。  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 プロジェクトでは、入れ子に対応し、プロジェクト項目のグループを作成するコレクションを使用します。 次のような階層が表示されます。  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 入れ子。 つまり、<xref:EnvDTE.ProjectItem>オブジェクトを指定できます<xref:EnvDTE.ProjectItems>と同時にコレクションため、`ProjectItems`コレクションは、入れ子になったオブジェクトを含めることができます。 基本的なプロジェクト サンプルには、この入れ子は示しません。 実装することによって、`Project`全体的なオートメーション モデルのデザインの特性を設定するツリーに似た構造に参加するオブジェクトします。  
  
 プロジェクトの自動化では、次の図に、パスに従います。  
  
 ![Visual Studio プロジェクト オブジェクト](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
プロジェクトの自動化  
  
 実装していない場合、`Project`オブジェクト、環境からジェネリック型の戻りが`Project`プロジェクトの名前のみを含むオブジェクト。  
  
## <a name="see-also"></a>関連項目  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>

