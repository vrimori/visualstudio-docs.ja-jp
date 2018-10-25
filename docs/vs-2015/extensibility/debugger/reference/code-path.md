---
title: CODE_PATH |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf8326fe1434b65293dc19de9da64a9a39327e39
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844606"
---
# <a name="codepath"></a>CODE_PATH
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

メソッドまたは関数呼び出しをについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
typedef struct tagCODE_PATH {   
   BSTR                bstrName;  
   IDebugCodeContext2* pCode;  
} CODE_PATH;  
```  
  
```csharp  
public struct CODE_PATH {  
   public string            bstrName;  
   public IDebugCodeContext pCode;  
}  
```  
  
## <a name="members"></a>メンバー  
 bstrName  
 コード パスの名前。  
  
 pCode  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)を関数にステップ インするコードのどこを識別するオブジェクト。  
  
## <a name="remarks"></a>Remarks  
 この構造体は、関数にステップ インを実装するために使用されます。 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)デバッグ中のプログラムの現在の場所から、すべての呼び出しを返します。 この構造体は、このような 1 回の呼び出しを表します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)

