---
title: "IDebugCoreServer3::EnableAutoAttach | Microsoft Docs"
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
  - "IDebugCoreServer3::EnableAutoAttach"
helpviewer_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定のデバッグ エンジンの自動アタッチを有効にします。  
  
## 構文  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```c#  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### パラメーター  
 `rgguidSpecificEngines`  
 \[入力\] 自動アタッチしてマークする各デバッグ エンジンの GUID の配列。  
  
 `celtSpecificEngines`  
 \[入力\] `rgguidSpecificEngines` で指定されたエンジンの数。  
  
 `pszStartPageUrl`  
 \[入力\] 自動アタッチするときに使用する開始 URL。  
  
 `pbstrSessionID`  
 \[入力\] 自動アタッチされたセッション ID。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  示す自動アタッチのクラス ファクトリを登録されていないという 1 種類のエラー コードを `E_AUTO_ATTACH_NOT_REGISTERED` です。  
  
## 解説  
 指定した URL に関連付けられているプログラムが起動されると指定されたデバッグ エンジンが自動的に開始され割り当てられます。  
  
## 参照  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)