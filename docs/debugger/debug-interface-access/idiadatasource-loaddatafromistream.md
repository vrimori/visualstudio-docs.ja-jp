---
title: "Idiadatasource::loaddatafromistream |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5babf70c1f7b58e85b681956c44f1e387441b8b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
メモリ内のデータ ストリームを使用してアクセス プログラム データベース (.pdb) ファイルに格納されているデバッグ データの準備を行います。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pIStream  
 [in]<xref:IStream>を使用するデータ ストリームを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 次の表は、このメソッドの戻り値を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|E_PDB_FORMAT|旧形式のファイルにアクセスしようとしています。|  
|E_INVALIDARG|Invalidparameter です。|  
|E_UNEXPECTED|データ ソースは、既に準備されています。|  
  
## <a name="remarks"></a>コメント  
 このメソッドにより、デバッグ データをメモリから取得される実行可能ファイルを<xref:IStream>オブジェクト。  
  
 検証を伴わない .pdb ファイルを読み込むを使用して、 [idiadatasource::loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)メソッドです。  
  
 特定の条件に対して .pdb ファイルを検証するを使用して、 [idiadatasource::loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)メソッドです。  
  
 アクセスするデータの読み込みプロセス (コールバック機構) を通じてを使用して、 [idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)メソッドです。  
  
## <a name="see-also"></a>参照  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource::loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)