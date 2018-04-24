---
title: IDiaDataSource |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5126ea6da80bb6c029f9237ff01dfc805c9eaf6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="idiadatasource"></a>IDiaDataSource
デバッグ シンボルのソースへのアクセスを開始します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaDataSource`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|最後の読み込みエラーのファイル名を取得します。|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|開き、デバッグ データ ソースとしてのプログラム データベース (.pdb) ファイルを用意します。|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|開き、プログラム データベース (.pdb) ファイルが提供されて署名情報と一致することを確認デバッグのデータ ソースとしての .pdb ファイルを準備します。|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|開き、.exe/.dll ファイルに関連付けられているデバッグ データの準備を行います。|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|メモリ内のデータ ストリームを使用してアクセス プログラム データベース (.pdb) ファイルに格納されているデバッグ データの準備を行います。|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|シンボルを照会するためのセッションを開きます。|  
  
## <a name="remarks"></a>コメント  
 いずれかの load メソッドの呼び出し、`IDiaDataSource`インターフェイスは、シンボル ファイルを開きます。 呼び出しは成功、 [idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)メソッドを返します、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)データ ソースのクエリをサポートするインターフェイスです。 Load メソッドがファイルに関連するエラーを返した場合、 [idiadatasource::get_lasterror](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)メソッドを返す値には、エラーに関連付けられているファイル名が含まれています。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは呼び出すことによって取得、`CoCreateInstance`クラス識別子を持つ関数`CLSID_DiaSource`とのインターフェイス ID`IID_IDiaDataSource`です。 この例では、このインターフェイスを取得する方法を示します。  
  
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
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)