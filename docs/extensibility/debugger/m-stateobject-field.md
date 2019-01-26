---
title: m_stateObject フィールド |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8718a45f0a2d8ef3075a9c390a756e3ec50062f9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028713"
---
# <a name="mstateobject-field"></a>m_stateObject フィールド
アクションを使用するデータを表すオブジェクト。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
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