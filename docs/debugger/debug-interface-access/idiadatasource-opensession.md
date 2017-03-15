---
title: "IDiaDataSource::openSession | Microsoft Docs"
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
  - "IDiaDataSource::openSession メソッド"
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

シンボルを照会するためのセッションを開きます。  
  
## 構文  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### パラメーター  
 ppSession  
 \[入力\] [IDiaSession](../../debugger/debug-interface-access/idiasession.md) を表すオブジェクトを公開審議返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  次の表はこのメソッドの有効な戻り値を示します。  
  
|値|Description|  
|-------|-----------------|  
|E\_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) のオブジェクトはシンボルのソースとして初期化されます。|  
|E\_INVALIDARG|`ppSession` の無効なパラメーター。|  
|E\_OUTOFMEMORY|セッションを開くメモリ不足。|  
  
## 解説  
 このメソッドはデータ ソースの [IDiaSession](../../debugger/debug-interface-access/idiasession.md) オブジェクトを開きます。  
  
 `IDiaSession` のオブジェクトはデータ ソースにクエリを実行します。  セッションはデバッグ シンボルの各セットの 1 種類のアドレス空間を管理します。  データ ソースのシンボルで記述された .exe または .dll ファイルが複数アドレス範囲で複数のアクティブ プロセスに読み込まれる場合があるため\(\) の場合各アドレスの範囲を 1 人のセッションを使用する必要があります。  
  
## 使用例  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## 参照  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)