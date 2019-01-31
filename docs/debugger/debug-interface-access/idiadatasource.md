---
title: IDiaDataSource |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97b55dad4ba557e85291d572ef24b1ad12e08a3c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930681"
---
# <a name="idiadatasource"></a>IDiaDataSource
デバッグ シンボルのソースへのアクセスを開始します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaDataSource`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|最後の読み込みエラーのファイル名を取得します。|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|開き、デバッグのデータ ソースとしてのプログラム データベース (.pdb) ファイルを準備します。|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|開き、プログラム データベース (.pdb) ファイルが提供されて署名情報と一致していることを確認します。デバッグのデータ ソースとしての .pdb ファイルを準備します。|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|開き、.exe/.dll ファイルに関連付けられたデバッグ データを準備します。|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|メモリ内のデータ ストリームを使用してアクセス プログラム データベース (.pdb) ファイルに格納されているデバッグ データを準備します。|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|シンボルを照会するためのセッションを開きます。|  
  
## <a name="remarks"></a>コメント  
 Load メソッドの 1 つの呼び出し、`IDiaDataSource`インターフェイスは、シンボル ファイルを開きます。 呼び出しは成功、 [idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)メソッドが返す、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)データ ソースの照会をサポートするインターフェイス。 Load メソッドは、ファイルに関連するエラーを返す場合、 [idiadatasource::get_lasterror](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)メソッドを返す値には、エラーに関連付けられているファイル名が含まれています。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは呼び出すことによって取得、`CoCreateInstance`クラス識別子を持つ関数`CLSID_DiaSource`とのインターフェイス ID`IID_IDiaDataSource`します。 この例では、このインターフェイスを取得する方法を示します。  
  
## <a name="example"></a>例  
  
```C++  
  
      IDiaDataSource* pSource;  
HRESULT hr = CoCreateInstance(CLSID_DiaSource,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaDataSource,  
                              (void**) &pSource);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>要件  
 ヘッダー:dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>「  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)