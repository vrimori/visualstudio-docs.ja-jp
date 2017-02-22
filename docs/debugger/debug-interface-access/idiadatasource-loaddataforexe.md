---
title: "IDiaDataSource::loadDataForExe | Microsoft Docs"
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
  - "IDiaDataSource::loadDataForExe メソッド"
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

を開き.exe\/.dll ファイルに関連付けられているデバッグ データを準備します。  
  
## 構文  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### パラメーター  
 実行可能ファイル  
 \[入力\] .exe ファイルまたは .dll ファイルへのパス。  
  
 searchPath  
 \[入力\] デバッグ データを検索する代替パス。  
  
 pCallback  
 \[入力\] [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)[IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)または [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) のインターフェイスなどのデバッグのコールバック インターフェイスをサポートするオブジェクトの `IUnknown` のインターフェイス。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  次の表はこのメソッドの使用可能なエラー コードの一部を示しています。  
  
|値|Description|  
|-------|-----------------|  
|E\_PDB\_NOT\_FOUND|ファイルを開きますいないかファイルに無効な書式指定があります。|  
|E\_PDB\_FORMAT|旧式の形式のファイルにアクセスしようとしました。|  
|E\_PDB\_INVALID\_SIG|シグネチャが一致しません。|  
|E\_PDB\_INVALID\_AGE|年齢が一致しません。|  
|E\_INVALIDARG|無効なパラメーター。|  
|E\_UNEXPECTED|データ ソースが既に用意されています。|  
  
## 解説  
 .exe\/.dll ファイル名のデバッグ ヘッダー関連付けられたデバッグ データの位置。  
  
 次にこのメソッドはデバッグのヘッダーを読み取りおよびは検索およびデバッグ データを準備します。  検索の進行状況はコールバックによってオプションで報告制御される場合があります。  たとえば[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) は `IDiaDataSource::loadDataForExe` のメソッドがデバッグ ディレクトリを探して処理するときです。  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) と [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) のインターフェイスはファイルが標準のファイル I\/O に直接アクセスできない場合に実行可能ファイルからのデータの読み込みの代替メソッドを提供するクライアント アプリケーションができます。  
  
 検証せずに .pdb ファイルを読み込むには[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) のメソッドを使用します。  
  
 特定の条件に対して .pdb ファイルを検証するには[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) のメソッドを使用します。  
  
 メモリの .pdb ファイルを直接読み込むには[IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) のメソッドを使用します。  
  
## 使用例  
  
```cpp#  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## 参照  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)