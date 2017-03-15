---
title: "IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs"
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
  - "IDiaDataSource::loadAndValidateDataFromPdb メソッド"
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

開きプログラム データベース \(.pdb\) ファイルが提供されている定義の情報と一致することを確認しデバッグ データ ソースとして .pdb ファイルを準備します。  
  
## 構文  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### パラメーター  
 `pdbPath`  
 \[入力\] .pdb ファイルへのパス。  
  
 `pcsig70`  
 \[入力\] .pdb ファイルの定義に対して検証する GUID の定義。  [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] の .pdb ファイルは後で GUID の定義があります。  
  
 `sig`  
 \[入力\] .pdb ファイルの定義に対して検証する 32 ビットの定義。  
  
 `age`  
 \[入力\] 検証する値を期日を経過してください。  期間は既知の時刻値必ずしも使用して.pdb ファイルが対応する .exe ファイルと同期するかどうかを確認するために対応しません。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  次の表はこのメソッドの有効な戻り値を示します。  
  
|値|Description|  
|-------|-----------------|  
|E\_PDB\_NOT\_FOUND|ファイルを開きますいないかファイルに無効な書式指定があります。|  
|E\_PDB\_FORMAT|旧式の形式のファイルにアクセスしようとしました。|  
|E\_PDB\_INVALID\_SIG|シグネチャが一致しません。|  
|E\_PDB\_INVALID\_AGE|年齢が一致しません。|  
|E\_INVALIDARG|無効なパラメーター。|  
|E\_UNEXPECTED|データ ソースが既に用意されています。|  
  
## 解説  
 .pdb ファイルは定義と時間の値の両方が含まれます。  これらの値は.pdb ファイルを検索する .dll ファイルまたは .exe にレプリケートされます。  データ ソースを準備する前にこのメソッドはという名前の .pdb ファイルの定義と期間が指定された値と一致することを確認します。  
  
 検証せずに .pdb ファイルを読み込むには[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) のメソッドを使用します。  
  
 データの読み込みプロセスにアクセスするにはコールバック機構を通じて[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) のメソッドを使用します。  
  
 メモリの .pdb ファイルを直接読み込むには[IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) のメソッドを使用します。  
  
## 使用例  
  
```cpp#  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## 参照  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)