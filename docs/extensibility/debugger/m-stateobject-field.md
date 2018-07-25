---
title: m_stateObject フィールド |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d33879ca8aaaba08288f9e16d54ab462d92f67b
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231318"
---
# <a name="mstateobject-field"></a>m_stateObject フィールド
アクションを使用するデータを表すオブジェクト。  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** mscorlib (で*mscorlib.dll*)  
  
 .NET Framework からこの内部メンバーにアクセスできないため、次の構文には共通中間言語 (CIL) が提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Remarks  
 これは、`state`パラメーター、<xref:System.Threading.Tasks.Task.%23ctor%2A>コンス トラクター。 バッキング フィールドも、<xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName>プロパティ。  
  
## <a name="see-also"></a>関連項目  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)