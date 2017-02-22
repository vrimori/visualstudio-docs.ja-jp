---
title: "IDiaEnumFrameData::frameByVA | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumFrameData::frameByVA メソッド"
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumFrameData::frameByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

仮想アドレスでフレームを返します \(VA\)。  
  
## 構文  
  
```cpp#  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### パラメーター  
 virtualAddress  
 \[入力\] 対象のフレームの VA。  
  
 フレーム  
 \[出力\] 指定したアドレスを含むフレームを表す [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` フレームのデータが指定したアドレスに一致する `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)