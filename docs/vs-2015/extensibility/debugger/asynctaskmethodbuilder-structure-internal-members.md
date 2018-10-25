---
title: AsyncTaskMethodBuilder 構造体の内部メンバー |Microsoft Docs
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
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b4f0c8cc8e011edb6f69b274816d295046bc76da
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210757"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder 構造体の内部メンバー
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックでの内部メンバーの説明、<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>クラス。 このクラスの詳細については、次を参照してください。、<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>リファレンス トピック。  
  
 **名前空間:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
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

