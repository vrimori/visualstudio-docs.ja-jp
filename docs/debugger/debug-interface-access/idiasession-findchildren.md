---
title: Idiasession::findchildren |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d2e0db2ec3f1f8f50dce061900ac086deca7777
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916283"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
指定した親の識別子の名前とシンボルの種類に一致するすべての子を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `parent`  
 [in][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)親を表すオブジェクト。 親シンボルは、関数、モジュール、またはブロックする場合でその構文の子が返されます`ppResult`します。 親のシンボルが、型の場合は、そのクラスの子が返されます。 このパラメーターが場合`NULL`、し`symtag`に設定する必要があります`SymTagExe`または`SymTagNull`、グローバル スコープ (.exe ファイル) が返されます。  
  
 `symtag`  
 [in]取得する子の記号のタグを指定します。 値から取得されます、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)列挙体。 設定`SymTagNull`をすべての子を取得します。  
  
 `name`  
 [in]取得する子の名前を指定します。 設定`NULL`のすべての子を取得します。  
  
 `compareFlags`  
 [in]名前の一致に適用される比較オプションを指定します。 値から、 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)列挙体は、単独または組み合わせて使用できます。  
  
 `ppResult`  
 [out]返します、 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)の子の記号の一覧を含むオブジェクトを取得します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="example"></a>例  
 次の例は、関数のローカル変数を検索する方法を示しています。`pFunc`その名前の一致`szVarName`します。  
  
```C++  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>「  
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)