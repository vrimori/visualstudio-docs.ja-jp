---
title: "IDebugErrorEvent2::GetErrorMessage |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 06ffcbaf1266f017b75e6c3662300096b534e209
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
人間が判読できるエラー メッセージの作成を許可する情報を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pMessageType`  
 [out]値を返します、 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)メッセージの種類を説明する列挙です。  
  
 `pbstrErrorFormat`  
 [out]ユーザーに最後のメッセージの形式 (詳細については、「解説」を参照してください)。  
  
 `hrErrorReason`  
 [out]エラー コード、メッセージは、に関するです。  
  
 `pdwType`  
 [out]エラーの重大度レベル (の MB_XXX 定数を使用して`MessageBox`。 たとえば、`MB_EXCLAMATION`または`MB_WARNING`)。  
  
 `pbstrHelpFileName`  
 [out]ヘルプ ファイル (ヘルプ ファイルがない場合は null 値に設定) へのパス。  
  
 `pdwHelpId`  
 [out](ヘルプ トピックがない場合は 0 に設定) を表示するヘルプ トピックの ID。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 エラー メッセージの書式はの線に沿った`"What I was doing.  %1"`です。 `"%1"`とエラー コードから派生した、エラー メッセージ、呼び出し元によって置き換えられますし (で返される`hrErrorReason`)。 `pMessageType`パラメーターは、最終的なエラー メッセージの表示方法を呼び出し元に通知します。  
  
## <a name="see-also"></a>参照  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)