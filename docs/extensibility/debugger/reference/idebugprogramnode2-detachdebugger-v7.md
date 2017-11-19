---
title: "IDebugProgramNode2::DetachDebugger_V7 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 84110c4e7d6a3e940df587811c24d4316f786cf4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
推奨されなくなりました。 使用しないでください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>戻り値  
 実装を常に返します`E_NOTIMPL`です。  
  
## <a name="remarks"></a>コメント  
  
> [!WARNING]
>  [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]、このメソッドは使用されなくを常に返す必要があります`E_NOTIMPL`です。  
  
 このメソッドは、デバッガーが突然終了するときに呼び出されます。 このメソッドが呼び出されたときに、DE は必要があります、ユーザーがそこからデタッチされたものとしてプログラムを再開します。 これ以上のデバッグ イベントを送信する必要があります。 プログラムは、デバッガーの別のインスタンスからアタッチ可能な状態である必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)