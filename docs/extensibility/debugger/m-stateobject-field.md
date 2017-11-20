---
title: "m_stateObject フィールド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85e8648fd757c6cdb7910123b3cd861f7abb3371
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="mstateobject-field"></a>m_stateObject フィールド
アクションが使用するデータを表すオブジェクト。  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** (mscorlib.dll) の mscorlib  
  
 .NET Framework からこの内部のメンバーにアクセスすることはできません、ため、次の構文は共通中間言語 (CIL) に提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>コメント  
 これは、`state`内のパラメーター、<xref:System.Threading.Tasks.Task.%23ctor%2A>コンス トラクターです。 バッキング フィールドも、<xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName>プロパティです。  
  
## <a name="see-also"></a>関連項目  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)