---
title: "IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs"
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
  - "IPropertyProxyEESide::CreateReplacementObject"
helpviewer_keywords: 
  - "IPropertyProxyEESide::CreateReplacementObject"
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

式エバリュエーターはデータ オブジェクトのコピーを作成します \(EE\)。  
  
## 構文  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### パラメーター  
 `dataIn`  
 \[入力\] コピーするデータを保持 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) のオブジェクト。  
  
 `dataOut`  
 \[入力\] `IEEDataStorage` の新しいオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドは [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) を表すオブジェクトをバイトの配列です。  この受信データ オブジェクトは EE によって通常は実行されません。  ただしこのメソッドによって返されるオブジェクトはEE を `IEEDataStorage` のインターフェイスを実装する EE によってクラスが必要な常に実行されます。  
  
 `IEEDataStorage` の入力オブジェクトが提供するデータが `IEEDataStorage` 出力データ オブジェクトの同じであることに注意してください。  
  
## 参照  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)