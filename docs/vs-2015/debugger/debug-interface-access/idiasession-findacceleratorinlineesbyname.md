---
title: IDiaSession::findAcceleratorInlineesByName |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b547d38779578ca4fc2fba44effc9b5a6037f4fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761840"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定されたインライン関数の名前に対応するインライン フレームのシンボルの列挙を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `name`  
 [in]検索するインライン関数の名前。  
  
 `option`  
 [in]対応しているフレームのインラインの検索時に使用される名前の検索オプション`name`します。 詳細については、次を参照してください。 [NameSearchOptions 列挙型](../../debugger/debug-interface-access/namesearchoptions.md)します。  
  
 `ppResult`  
 [out]ポインター、`IDiaEnumSymbols`インターフェイス ポインターでは、結果を使用して初期化します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 この関数はインラインに起因アクセラレータ スタブ関数内でのみを検索します。 ネイティブ C++ プロシージャ レコードは無視されます。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



