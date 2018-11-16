---
title: m_children フィールド |Microsoft Docs
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
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f044c2dae278a0656f1f9e4c41a3940d87658a64
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731043"
---
# <a name="mchildren-field"></a>m_children フィールド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このタスクで登録されている子タスクの一覧。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** mscorlib (mscorlib.dll 内)  
  
 .NET Framework からこの内部メンバーにアクセスできないため、次の構文には共通中間言語 (CIL) が提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Remarks  
 タスクの実行中にタスクを実行するスレッドのみがこの配列をアクセスする必要があります。  
  
 タスクが完了した場合、他のスレッドには何も追加またはからそのすべてを削除する操作を行いますがない限りこのフィールドにアクセスすることができます。  
  
## <a name="see-also"></a>関連項目  
 [ContingentProperties クラス](../../extensibility/debugger/contingentproperties-class-internal-members.md)

