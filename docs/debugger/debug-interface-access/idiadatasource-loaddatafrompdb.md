---
title: Idiadatasource::loaddatafrompdb |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0cc7ce21633fc4f7cb5ad3f4dff141a7a0e46d3b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023016"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
開き、デバッグのデータ ソースとしてのプログラム データベース (.pdb) ファイルを準備します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pdbPath  
 [in].Pdb ファイルへのパス。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 次の表では、このメソッドの戻り値を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|ファイルを開いてに失敗したか、ファイルが無効な形式であることを確認します。|  
|E_PDB_FORMAT|旧形式のファイルにアクセスしようとしています。|  
|E_INVALIDARG|無効なパラメーター。|  
|E_UNEXPECTED|データ ソースは既に準備されています。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、.pdb ファイルから直接デバッグ データを読み込みます。  
  
 特定の条件に対して、.pdb ファイルを検証するには、使用、 [idiadatasource::loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)メソッド。  
  
 (コールバック機構) を通じてデータの読み込みプロセスにアクセスを使用して、 [idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)メソッド。  
  
 .Pdb ファイルをメモリから直接読み込むには使用、 [idiadatasource::loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)メソッド。  
  
## <a name="example"></a>例  
  
```C++  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## <a name="see-also"></a>「  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)