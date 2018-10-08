---
title: CANSTOP_REASON |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ea8242e4c7bdd820dd30cfb2c86cde60cda8bcd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544995"
---
# <a name="canstopreason"></a>CANSTOP_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CANSTOP_REASON](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/canstop-reason)します。  
  
プログラムが実行の特定のポイントに到達した後の実行を停止するかどうかを判断するために使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>メンバー  
 CANSTOP_ENTRYPOINT  
 特定のプログラムのエントリ ポイントを指定します。  
  
 CANSTOP_STEPIN  
 関数にステップ インを指定します。  
  
## <a name="remarks"></a>Remarks  
 引数として渡される、 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)セッション デバッグ マネージャー (SDM) の場合は、プログラムのエントリ ポイントに到達した後、または関数またはメソッドにステップ インした後に停止しても問題をことを確認します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)

