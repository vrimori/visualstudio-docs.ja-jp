---
title: Idiadatasource::get_lasterror |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08d17e0532d4d5d987d69afa7de062a193371950
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
最後の読み込みエラーのファイル名を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pRetVal  
 [out]最後の読み込みエラーに関連付けられている .pdb ファイルの名前を含む文字列を返します。  
  
## <a name="return-value"></a>戻り値  
 ロード操作によって発生した最後のエラー コードを返します。 返します`E_INVALIDARG`場合、`pRetVal`パラメーターは`NULL`します。  
  
## <a name="example"></a>例  
  
```C++  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>関連項目  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)