---
title: MESSAGETYPE |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fa09d938e0e7c3853431369c7e0634242df2ee0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31124831"
---
# <a name="messagetype"></a>MESSAGETYPE
メッセージの種類および理由を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>メンバー  
 MT_OUTPUTSTRING  
 出力ウィンドウにメッセージを送信する必要がありますされることを示します。 これはから相互に排他的な`MT_MESSAGEBOX`します。  
  
 MT_MESSAGEBOX  
 メッセージ ボックスに、メッセージを表示するかを示します。 これはから相互に排他的な`MT_OUTPUTSTRING`します。  
  
 MT_TYPE_MASK  
 メッセージの送信先を分離するマスクの値。  
  
 MT_REASON_EXCEPTION  
 例外の結果として、メッセージ ボックスが表示されていることを示します。 これはから相互に排他的な`MT_REASON_TRACEPOINT`します。  
  
 MT_REASON_TRACEPOINT  
 トレース ポイントをヒットした結果として、メッセージ ボックスが表示されていることを示します。 これは、相互に排他的`MT_REASON_EXCEPTION`です。  
  
 MT_REASON_MASK  
 マスクの値を表示されているメッセージの原因を特定します。  
  
## <a name="remarks"></a>コメント  
 これらの値から返される、 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)と[GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)メソッドです。  
  
 理由の値のいずれかと組み合わせて使用できます、出力先を使用して値、ビットごとの 1 つ`OR`です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [getMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)