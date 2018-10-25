---
title: ATTACH_REASON |Microsoft Docs
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
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff2c71418f3586c2915f1d4f4f4ff2fe37ed9bf4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873605"
---
# <a name="attachreason"></a>ATTACH_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

プログラム ノードにアタッチするデバッグ エンジン (DE) の理由を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```csharp  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>メンバー  
 ATTACH_REASON_AUTO  
 プロセスがデバッグ モードでは現在ためにをアタッチします。  
  
 ATTACH_REASON_LAUNCH  
 プロセスが起動されているため、接続します。  
  
 ATTACH_REASON_USER  
 ユーザーの要求によりアタッチします。  
  
## <a name="remarks"></a>Remarks  
 これらの値がパラメーターとして使用される、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)と[アタッチ](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [添付](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)

