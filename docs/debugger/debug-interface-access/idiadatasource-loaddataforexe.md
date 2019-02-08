---
title: Idiadatasource::loaddataforexe |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13b852e917e55803fd37687ced86f819e0b591e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961040"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
開き、.exe/.dll ファイルに関連付けられたデバッグ データを準備します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 executable  
 [in].Exe または .dll ファイルへのパス。  
  
 検索パス  
 [in]デバッグ データを検索するパス。  
  
 pCallback  
 [in]`IUnknown`など、デバッグのコールバック インターフェイスをサポートするオブジェクトのインターフェイスを[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)、 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)、 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)、または[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)インターフェイス。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 次の表では、このメソッドの想定されるエラー コードの一部を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|ファイルを開いて、できなかったか、ファイルがの形式が無効です。|  
|E_PDB_FORMAT|旧形式のファイルにアクセスしようとしています。|  
|E_PDB_INVALID_SIG|署名が一致しません。|  
|E_PDB_INVALID_AGE|年齢が一致しません。|  
|E_INVALIDARG|無効なパラメーター。|  
|E_UNEXPECTED|データ ソースは既に準備されています。|  
  
## <a name="remarks"></a>コメント  
 .Exe/.dll ファイルのデバッグ ヘッダー名を関連するデバッグ データの場所。  
  
 このメソッドは、デバッグ ヘッダーを読み取りとし、検索し、デバッグ データを準備します。 検索の進行状況の報告されコールバックをとおして制御されます、必要に応じて、可能性があります。 たとえば、 [idialoadcallback::notifydebugdir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)が呼び出されたときに、`IDiaDataSource::loadDataForExe`を検索して、デバッグ ディレクトリを処理します。  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)と[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)インターフェイスは、実行可能ファイルからデータを読み取るための代替方法を提供するクライアント アプリケーションを使用するファイルのファイル標準的なファイル I/O を介して直接アクセスできません。  
  
 検証を伴わない .pdb ファイルを読み込むには、使用、 [idiadatasource::loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)メソッド。  
  
 特定の条件に対して、.pdb ファイルを検証するには、使用、 [idiadatasource::loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)メソッド。  
  
 .Pdb ファイルをメモリから直接読み込むには使用、 [idiadatasource::loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)メソッド。  
  
## <a name="example"></a>例  
  
```C++  
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
  
## <a name="see-also"></a>関連項目
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
