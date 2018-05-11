---
title: Idiasymbol::get_undecoratednameex |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 078826c799cf99cadd1812ff88dc29663a759baf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
C++ の非装飾の名前の取得の一部またはすべての装飾 (リンケージ) 名です。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `undecoratedOptions`  
 [in]返される結果を制御するフラグの組み合わせを指定します。 特定の値とその実行内容の「解説」セクションを参照してください。  
  
 `pRetVal`  
 [out]C++ の装飾されていない名前の装飾名を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値の`S_FALSE`プロパティは、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>コメント  
 `undecorateOptions`次のフラグの組み合わせが可能です。  
  
> [!NOTE]
>  フラグ名は、コードに、宣言を追加するか、生の値を使用する必要がありますので DIA SDK で定義されていません。  
  
|フラグ|値|説明|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Undecoration を完全に有効にします。|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Microsoft 拡張キーワードの先頭のアンダー スコアを削除します。|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Microsoft 拡張キーワードの拡張を無効にします。|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|プライマリの宣言の戻り値の型の拡張を無効にします。|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|宣言のモデルの拡張を無効にします。|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|宣言の言語指定子の拡張を無効にします。|  
|UNDNAME_RESERVED1|0x0020|予約されています。|  
|UNDNAME_RESERVED2|0x0040|予約されています。|  
|UNDNAME_NO_THISTYPE|0x0060|すべての修飾子で無効にして、`this`型です。|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|メンバーのアクセス指定子の拡張を無効にします。|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|「Throw 署名」の関数および関数へのポインターの拡張を無効にします。|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|拡張を無効に`static`または`virtual`メンバー。|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|UDT を返します、Microsoft のモデルの拡張を無効にします。|  
|UNDNAME_32_BIT_DECODE|0x0800|32 ビットの装飾名を undecorates です。|  
|UNDNAME_NAME_ONLY|0x1000|プライマリの宣言の名前のみを取得します。だけを返します [スコープ::] の名前。  テンプレート パラメーターを展開します。|  
|UNDNAME_TYPE_ONLY|0x2000|入力がエンコード; 種類のみ抽象宣言子を構成します。|  
|UNDNAME_HAVE_PARAMETERS|0x4000|実際のテンプレート パラメーターは、使用できます。|  
|UNDNAME_NO_ECSU|0x8000|列挙型/クラス/構造体/共用体を抑制します。|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|有効な識別子の文字のチェックを抑制します。|  
|UNDNAME_NO_PTR64|0x20000|出力に ptr64 は含まれません。|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)