---
title: AsyncTaskMethodBuilder 構造体の内部メンバー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14b17ebde347d2558c8d18277d5c49d066243034
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548159"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder 構造体の内部メンバー
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[AsyncTaskMethodBuilder 構造体の内部メンバー](https://docs.microsoft.com/visualstudio/extensibility/debugger/asynctaskmethodbuilder-structure-internal-members)します。  
  
このトピックでの内部メンバーの説明、<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>クラス。 このクラスの詳細については、次を参照してください。、<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>リファレンス トピック。  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **アセンブリ:** mscorlib (mscorlib.dll 内)  
  
 .NET Framework からこれらの内部メンバーにアクセスできないため、次の構文には共通中間言語 (CIL) が提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>内部メンバー  
  
|名前|説明|  
|----------|-----------------|  
|[ObjectIdForDebugger プロパティ](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|デバッガーには、このビルダーを一意に識別するために使用するオブジェクトを取得します。|  
|[m_builder フィールド](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|この非ジェネリック インスタンスをデリゲートする汎用ビルダー オブジェクトを表します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [.NET Framework の並列拡張機能の内部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

