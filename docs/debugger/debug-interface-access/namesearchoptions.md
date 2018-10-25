---
title: NameSearchOptions |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c4b8771ad1bf2ee97ec1f22636a4684bc9aa7ee8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950343"
---
# <a name="namesearchoptions"></a>NameSearchOptions
シンボルとファイル名の検索オプションを指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## <a name="elements"></a>Elements  
 `nsNone`  
 オプションは指定されていません。  
  
 `nsfCaseSensitive`  
 大文字小文字を区別する名前の一致を適用します。  
  
 `nsfCaseInsensitive`  
 大文字の名前の一致を適用します。  
  
 `nsfFNameExt`  
 パスと名前を処理し、.ext という名前の一致を適用します。  
  
 `nsfRegularExpression`  
 ワイルドカードとしてアスタリスク (*) や疑問符 (?) を使用して区別する名前の一致を適用します。  
  
 `nsfUndecoratedName`  
 装飾されていないし、装飾名がシンボルにのみ適用されます。  
  
## <a name="remarks"></a>Remarks  
 この列挙の値は、次のメソッドに渡されます。  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: dia2.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasession::findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Idiasession::findfile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)