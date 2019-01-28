---
title: m_children フィールド |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f8ea4f053d28ea14c05a50e3bc187faf6f6e207
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966856"
---
# <a name="mchildren-field"></a>m_children フィールド
このタスクで登録されている子タスクの一覧。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** mscorlib (で*mscorlib.dll*)  
  
 .NET Framework からこの内部メンバーにアクセスできないため、次の構文には共通中間言語 (CIL) が提供されます。  
  
## <a name="syntax"></a>構文  
  
```csharp 
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Remarks  
 タスクの実行中にタスクを実行するスレッドのみがこの配列をアクセスする必要があります。  
  
 タスクが完了した場合、他のスレッドには何も追加またはそこから何も削除されない限り、このフィールドにアクセスすることができます。  
  
## <a name="see-also"></a>関連項目  
 [ContingentProperties クラス](../../extensibility/debugger/contingentproperties-class-internal-members.md)