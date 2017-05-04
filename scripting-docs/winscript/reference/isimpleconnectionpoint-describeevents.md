---
title: "ISimpleConnectionPoint::DescribeEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.DescribeEvents
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::DescribeEvents"
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::DescribeEvents
イベントの指定範囲の各イベントの DISPID と名前を返します。  
  
## 構文  
  
```  
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### パラメーター  
 `iEvent`  
 \[入力\]取得する最初のイベントのインデックス。  
  
 `cEvents`  
 \[入力\]取得するイベントの数。  
  
 `prgid`  
 \[入力\]イベントの DISPID 値の配列。  
  
 `prgbstr`  
 \[入力\]イベント名の配列。  
  
 `pcEventsFetched`  
 \[入力\]フェッチ イベントの実際の数。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`S_FALSE`|イベントの詳細には使用可能になったより要求されました。  使用できないイベントは DISPID\_NULL および null BSTR と表されます。|  
|`E_INVALIDARG`|要素をフェッチことができませんでした。|  
  
## 解説  
 このメソッドは、イベントの指定範囲の各イベントの DISPID と名前を返します。  
  
## 参照  
 [ISimpleConnectionPoint インターフェイス](../../winscript/reference/isimpleconnectionpoint-interface.md)