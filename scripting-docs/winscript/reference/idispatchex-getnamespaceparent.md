---
title: "IDispatchEx::GetNameSpaceParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNameSpaceParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetNameSpaceParent メソッド"
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNameSpaceParent
オブジェクトの名前空間の親のインターフェイスを取得します。  
  
## 構文  
  
```  
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### パラメーター  
 `ppunk`  
 名前空間の親のインターフェイスを受け取る `IUnknown` のインターフェイス ポインターのアドレス。  
  
## 戻り値  
 または OLE 定義のエラー コード別の方法で成功した場合 `S_OK` を返します。  
  
## 参照  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)