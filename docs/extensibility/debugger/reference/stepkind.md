---
title: "STEPKIND |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3a2b82bb70aa7bcf41dc6c8c827c318d78cf394e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="stepkind"></a>STEPKIND
ステップ実行のステップの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```csharp  
public enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
```  
  
## <a name="members"></a>メンバー  
 STEP_INTO  
 関数にステップ インします。  
  
 STEP_OVER  
 関数に対する手順を説明します。  
  
 STEP_OUT  
 関数から手順を説明します。  
  
 STEP_BACKWARDS  
 関数には旧バージョンと手順。  
  
## <a name="remarks"></a>コメント  
 引数として渡される、[ステップ](../../../extensibility/debugger/reference/idebugprocess3-step.md)メソッドです。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)