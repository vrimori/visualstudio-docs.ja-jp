---
title: Idiasession::findchildren |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97fed0f8ce7ff0712054b2aa3408217efe39f706
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534062"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[idiasession::findchildren](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-findchildren)します。  
  
指定した親の識別子の名前とシンボルの種類に一致するすべての子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>関連項目  
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)



