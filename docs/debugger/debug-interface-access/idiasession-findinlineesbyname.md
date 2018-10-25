---
title: IDiaSession::findInlineesByName |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 9860336d-f703-4ecb-bfc4-3f5beb175a76
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47d01237d7e2235f2d50e82a8fd599384e930d2c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896264"
---
# <a name="idiasessionfindinlineesbyname"></a>IDiaSession::findInlineesByName
により、クライアントは、指定した名前と一致するすべてのインライン関数の行番号情報を反復処理する列挙体を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT findInlineesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `name`  
 [in]比較に使用する名前を指定します。  
  
 `option`  
 [in]名前の検索に適用される比較オプションを指定します。 値から、 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)列挙体は、単独または組み合わせて使用できます。  
  
 `ppResult`  
 [out]返します、 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)取得された行番号の一覧を含むオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)