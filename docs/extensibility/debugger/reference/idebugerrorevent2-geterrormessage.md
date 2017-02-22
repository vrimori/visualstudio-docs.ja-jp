---
title: "IDebugErrorEvent2::GetErrorMessage | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
helpviewer_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

情報をユーザーが認識できるエラー メッセージの構築を利用できる返します。  
  
## 構文  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```c#  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### パラメーター  
 `pMessageType`  
 \[入力\] メッセージの種類を示す [メッセージの種類](../../../extensibility/debugger/reference/messagetype.md) の列挙型の値を返します。  
  
 `pbstrErrorFormat`  
 \[入力\] ユーザーに最終的なメッセージの形式 \(詳細については「解説」を参照してください\)。  
  
 `hrErrorReason`  
 \[入力\] エラー コードはメッセージ通知します。  
  
 `pdwType`  
 \[入力\] エラーの重大度レベル \(`MessageBox` に MB\_XXX の定数を使用してください ; たとえば`MB_EXCLAMATION` または `MB_WARNING`\)。  
  
 `pbstrHelpFileName`  
 \[入力\] ヘルプ ファイルがない場合はヘルプ ファイルへのパス \(null 値に設定します。  
  
 `pdwHelpId`  
 \[入力\] ヘルプ トピックがある\) 表示するヘルプ トピック ID \(0 に設定します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 エラー メッセージが `"What I was doing. %1"` に従って書式指定する必要があります。  `"%1"` \(`hrErrorReason` でエラー メッセージが呼び出し元によって返されるエラー コードから派生\) に置き換えられます。  `pMessageType` のパラメーターは最終的なエラー メッセージを表示するかを呼び出し元に通知します。  
  
## 参照  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [メッセージの種類](../../../extensibility/debugger/reference/messagetype.md)