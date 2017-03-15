---
title: "IDiaFrameData::execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaFrameData::execute メソッド"
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

スタック アンワインドを実行しスタック ウォークのフレームのインターフェイスの結果を返します。  
  
## 構文  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### パラメーター  
 `frame`  
 \[入力\] フレームの状態を保持します [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) のオブジェクトを登録します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  次の表はこのメソッドの有効な戻り値を示します。  
  
|値|Description|  
|-------|-----------------|  
|E\_DIA\_INPROLOG|がプロローグ コードのスタック フレームを実行できません。|  
|E\_DIA\_SYNTAX|フレームのプログラムにある解析エラー。|  
|E\_DIA\_FRAME\_ACCESS|レジスタまたはメモリにアクセスできません。|  
|E\_DIA\_VALUE|値の計算 \(除算\) のエラー。|  
  
## 解説  
 このメソッドはデバッグ時のスタックをアンワインドするために呼び出されます。  [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) のオブジェクトは更新を登録して受け取り`execute` のメソッドで使用されるメソッドを提供するクライアント アプリケーションによって実装されます。  
  
## 参照  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)