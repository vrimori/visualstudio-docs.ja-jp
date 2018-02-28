---
title: "Idiadatasource::loadandvalidatedatafrompdb |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bcd82116c7499d2a2289fc0c198a2be053226721
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
開きますと、プログラム データベース (.pdb) ファイルと一致する、提供された署名情報を確認し、デバッグ データ ソースとしての .pdb ファイルを準備します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdbPath`  
 [in].Pdb ファイルへのパス。  
  
 `pcsig70`  
 [in].Pdb ファイルの署名を検証する GUID の署名。 ファイルを .pdb のみ[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]GUID の署名を後であるとします。  
  
 `sig`  
 [in]32 ビット署名を検証します .pdb ファイルの署名を照合します。  
  
 `age`  
 [in]値を確認する期間を表します。 保存期間は必ずしも対応しません既知の時刻値には、.pdb ファイルが対応する .exe ファイルとの同期であるかを判断するために使用されます。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 次の表は、このメソッドの戻り値を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|開くには、ファイルが失敗したか、ファイルに形式が無効です。|  
|E_PDB_FORMAT|旧形式のファイルにアクセスしようとしています。|  
|E_PDB_INVALID_SIG|署名が一致しません。|  
|E_PDB_INVALID_AGE|有効期間は一致しません。|  
|E_INVALIDARG|無効なパラメーター。|  
|E_UNEXPECTED|データ ソースは、既に準備されています。|  
  
## <a name="remarks"></a>コメント  
 .Pdb ファイルには、署名と有効期間の両方の値が含まれています。 これらの値は、.pdb ファイルに対応する .exe または .dll ファイルでレプリケートされます。 データ ソースを準備する前に、このメソッドは、名前付きの .pdb ファイルの署名と経過日数が指定された値を一致を確認します。  
  
 検証を伴わない .pdb ファイルを読み込むを使用して、 [idiadatasource::loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)メソッドです。  
  
 アクセスするデータの読み込みプロセス (コールバック機構) を通じてを使用して、 [idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)メソッドです。  
  
 メモリから直接読み込む .pdb ファイルを使用して、 [idiadatasource::loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)メソッドです。  
  
## <a name="example"></a>例  
  
```C++  
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
  
## <a name="see-also"></a>参照  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource::loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)