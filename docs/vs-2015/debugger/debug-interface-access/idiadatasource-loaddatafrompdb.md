---
title: Idiadatasource::loaddatafrompdb |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dd4700ba658aec5dd2cd59858cc243a7d79a523
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752826"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

開き、デバッグのデータ ソースとしてのプログラム データベース (.pdb) ファイルを準備します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
## <a name="remarks"></a>Remarks  
 このメソッドは、.pdb ファイルから直接デバッグ データを読み込みます。  
  
 特定の条件に対して、.pdb ファイルを検証するには、使用、 [idiadatasource::loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)メソッド。  
  
 (コールバック機構) を通じてデータの読み込みプロセスにアクセスを使用して、 [idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)メソッド。  
  
 .Pdb ファイルをメモリから直接読み込むには使用、 [idiadatasource::loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)メソッド。  
  
## <a name="example"></a>例  
  
```cpp#  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource::loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)



