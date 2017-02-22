---
title: "IDiaDataSource::loadDataFromPdb | Microsoft Docs"
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
  - "IDiaDataSource::loadDataFromPdb メソッド"
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

を開きデバッグ データ ソースとしてプログラム データベース \(.pdb\) ファイルを準備します。  
  
## 構文  
  
```cpp#  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### パラメーター  
 pdbPath  
 \[入力\] .pdb ファイルへのパス。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  次の表はこのメソッドの有効な戻り値を示します。  
  
|値|Description|  
|-------|-----------------|  
|E\_PDB\_NOT\_FOUND|またはファイルを開きますいないかファイルに無効な書式指定があると判断しました。|  
|E\_PDB\_FORMAT|旧式の形式のファイルにアクセスしようとしました。|  
|E\_INVALIDARG|無効なパラメーター。|  
|E\_UNEXPECTED|データ ソースが既に用意されています。|  
  
## 解説  
 このメソッドは.pdb ファイルからデバッグ直接データを読み込みます。  
  
 特定の条件に対して .pdb ファイルを検証するには[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) のメソッドを使用します。  
  
 データの読み込みプロセスにアクセスするにはコールバック機構を通じて[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) のメソッドを使用します。  
  
 メモリの .pdb ファイルを直接読み込むには[IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) のメソッドを使用します。  
  
## 使用例  
  
```cpp#  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## 参照  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)