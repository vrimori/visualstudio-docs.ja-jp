---
title: "IDebugPortRequest2::GetPortName | Microsoft Docs"
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
  - "IDebugPortRequest2::GetPortName"
helpviewer_keywords: 
  - "IDebugPortRequest2::GetPortName"
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ポートの名前を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```c#  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### パラメーター  
 `pbstrPortName`  
 \[入力\] ポートの名前を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) のデバッグ インターフェイスは通常パッケージ \(クライアント\) のポートのサプライヤー \(サーバー\) とポートへの接続を取得するために渡されます。  デバッグの両方のパッケージとポートの業者はポートの使用可能な選択に認識しています。  単純な文字列がポートについて `IDebugPortRequest2::GetPortName` の場合にメソッドを関連付けるための十分な情報があります。  それ以外の場合は追加のインターフェイスは `IDebugPortRequest2::QueryInterface` を使用してサーバー上で取得できるクライアントに提供できます。  
  
## 参照  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)