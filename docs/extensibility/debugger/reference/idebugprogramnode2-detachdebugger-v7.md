---
title: "IDebugProgramNode2::DetachDebugger_V7 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ea8843a824eb5e1cd0c7bcd658908d7cdaac98ce
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
使用されなくなりました。 使用しないでください。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```c#  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>戻り値  
 常に、実装を返さなければ`E_NOTIMPL`します。  
  
## <a name="remarks"></a>コメント  
  
> [!WARNING]
>  現在の[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]、このメソッドは、使用を中止し、常に返す必要があります`E_NOTIMPL`します。  
  
 デバッガーが予期せず終了するときに、このメソッドが呼び出されます。 このメソッドが呼び出されたときに、DE は必要があります、ユーザーがそこからデタッチされたものとしてプログラムを再開します。 これ以上のデバッグ イベントを送信する必要があります。 プログラムが、デバッガーの別のインスタンスからアタッチ可能な状態である必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
