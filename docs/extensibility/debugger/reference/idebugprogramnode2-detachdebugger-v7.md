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
ms.workload: vssdk
ms.openlocfilehash: af2f9e5851e53c86fb5466e7fc2cdfe515b5fb21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)