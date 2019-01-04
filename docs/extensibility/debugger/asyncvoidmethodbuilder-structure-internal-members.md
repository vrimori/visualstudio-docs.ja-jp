---
title: AsyncVoidMethodBuilder 構造体の内部メンバー |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4aa6a9ab426f3773e7885b449a4b91b284cc0f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875113"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder 構造体の内部メンバー
このトピックでの内部メンバーの説明、<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>クラス。 このクラスの詳細については、次を参照してください。、<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>リファレンス トピック。  
  
 **名前空間:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **アセンブリ:** mscorlib (mscorlib.dll 内)  
  
 .NET Framework からこれらの内部メンバーにアクセスできないため、次の構文には共通中間言語 (CIL) が提供されます。  
  
## <a name="syntax"></a>構文  
  
```csharp  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>内部メンバー  
  
|名前|説明|  
|----------|-----------------|  
|[ObjectIdForDebugger プロパティ](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|デバッガーには、このビルダーを一意に識別するために使用するオブジェクトを取得します。|  
|[m_objectIdForDebugger フィールド](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|このビルダーを一意に識別するために、デバッガーによって使用される遅れて初期化されるオブジェクトを表します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [.NET Framework の並列拡張機能の内部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)