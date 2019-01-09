---
title: IDebugExpressionContext::ParseLanguageText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a55dc9ae2ae92a76c2b426d1f36949573b37a265
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087725"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
指定したテキストのデバッグの式を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrCode`  
 [in]式またはステートメントのテキストを提供します。  
  
 `nRadix`  
 [入力] 使用する基数。  
  
 `pstrDelimiter`  
 [in]最後のスクリプト ブロックの区切り記号。 ときに`pstrCode`解析は、テキストのストリームからホスト通常などの使用、区切り記号、2 つの単一引用符 (")、スクリプト ブロックの終わりを検出します。 このパラメーターには、ホストが使用する区切り文字を指定します。それにより、スクリプト エンジンで何らかの条件付きのプリミティブな前処理が可能になります (単一引用符 (') を区切り文字として使用するために 2 つの単一引用符に置き換えるなど)。 正確に把握 (および場合は) この情報は、スクリプト エンジンによって異なります、スクリプト エンジンが使用されます。 このパラメーターに設定`NULL`ホストは、スクリプト ブロックの終わりをマークする、区切り記号を使用しなかった場合。  
  
 `dwFlags`  
 [in]次のデバッグ テキスト フラグの組み合わせ。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|テキストがステートメントではなく式であることを示します。 このフラグは、一部の言語によるテキストの解析方法に影響する場合があります。|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|戻り値が使用できる場合、その値は呼び出し元によって使用されます。|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|副作用は許可されません。 このフラグが設定されている場合は、ランタイム状態が式の評価によって変更されることはありません。|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|テキスト評価中にブレークポイントを使用できます。 このフラグが設定されていない場合、ブレークポイントは、テキストの評価時に無視されます。|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|テキスト評価中にエラー レポートを使用します。 このフラグが設定されていない場合、エラーは報告されませんホストを評価中にします。|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|式自体を実行しているのではなく、コードのコンテキストに評価される式を示します|  
  
 `ppe`  
 [out]指定したテキストをデバッグの式を返します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、指定したテキストのデバッグの式を作成します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpressionContext インターフェイス](../../winscript/reference/idebugexpressioncontext-interface.md)