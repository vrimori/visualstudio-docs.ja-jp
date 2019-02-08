---
title: Idiadatasource::loadandvalidatedatafrompdb |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 88bb10e46d9007878282338aff0379c57eca2aba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911703"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
開き、プログラム データベース (.pdb) ファイルに指定すると、署名情報と一致することを確認しますと、デバッグのデータ ソースとしての .pdb ファイルを準備します。  
  
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
 [in].Pdb ファイルの署名を検証する 32 ビットの署名。  
  
 `age`  
 [in]保存期間の値を確認します。 任意の既知の時刻値に、年齢が必ずしも対応していない、.pdb ファイルが対応する .exe ファイルと同期していないかを判断するために使用されます。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 次の表では、このメソッドの戻り値を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|ファイルを開いて、できなかったか、ファイルがの形式が無効です。|  
|E_PDB_FORMAT|旧形式のファイルにアクセスしようとしています。|  
|E_PDB_INVALID_SIG|署名が一致しません。|  
|E_PDB_INVALID_AGE|年齢が一致しません。|  
|E_INVALIDARG|無効なパラメーター。|  
|E_UNEXPECTED|データ ソースは既に準備されています。|  
  
## <a name="remarks"></a>コメント  
 .Pdb ファイルには、署名と経過時間の両方の値が含まれています。 これらの値は、.pdb ファイルに一致する .exe または .dll ファイルにレプリケートされます。 データ ソースを準備する前に、このメソッドは、名前付きの .pdb ファイルの署名と保存期間が指定された値と一致するを確認します。  
  
 検証を伴わない .pdb ファイルを読み込むには、使用、 [idiadatasource::loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)メソッド。  
  
 (コールバック機構) を通じてデータの読み込みプロセスにアクセスを使用して、 [idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)メソッド。  
  
 .Pdb ファイルをメモリから直接読み込むには使用、 [idiadatasource::loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)メソッド。  
  
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
  
## <a name="see-also"></a>関連項目
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
