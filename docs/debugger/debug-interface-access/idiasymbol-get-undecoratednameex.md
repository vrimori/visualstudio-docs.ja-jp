---
title: "IDiaSymbol::get_undecoratedNameEx | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_undecoratedNameEx メソッド"
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

取得はは. の C\+\+ リンケージで修飾された名前 \(\) すべて非装飾名の部分。  
  
## 構文  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### パラメーター  
 `undecoratedOptions`  
 \[出力\] 返されるかを制御するフラグの組み合わせを指定します。  処理を特定の値については" 解説 " を参照してください。  
  
 `pRetVal`  
 \[入力\] C.C\+\+ の装飾名の装飾名を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合戻り `S_FALSE` またはエラー コード。  
  
> [!NOTE]
>  `S_FALSE` の戻り値はプロパティのシンボルで使用できないことを意味します。  
  
## 解説  
 `undecorateOptions`次のフラグの組み合わせです。  
  
> [!NOTE]
>  フラグの名前は DIA SDK で定義されていない宣言をコードに追加すると基になる値を使用するため必要があります。  
  
|フラグ|値|Description|  
|---------|-------|-----------------|  
|UNDNAME\_COMPLETE|0x0000|有効な完全な undecoration。|  
|UNDNAME\_NO\_LEADING\_UNDERSCORES|0x0001|Microsoft から先頭にアンダースコア \(\) が拡張されたキーワードを削除します。|  
|UNDNAME\_NO\_MS\_KEYWORDS|0x0002|Microsoft の配置を拡張するキーワードを無効にします。|  
|UNDNAME\_NO\_FUNCTION\_RETURNS|0x0004|主要な宣言の戻り値の型の展開を無効にします。|  
|UNDNAME\_NO\_ALLOCATION\_MODEL|0x0008|宣言モデルの配置を無効にします。|  
|UNDNAME\_NO\_ALLOCATION\_LANGUAGE|0x0010|宣言の言語指定子の配置を無効にします。|  
|UNDNAME\_RESERVED1|0x0020|予約済み。|  
|UNDNAME\_RESERVED2|0x0040|予約済み。|  
|UNDNAME\_NO\_THISTYPE|0x0060|`this` の種類のすべての修飾子を無効にします。|  
|UNDNAME\_NO\_ACCESS\_SPECIFIERS|0x0080|メンバーのアクセス指定子の配置を無効にします。|  
|UNDNAME\_NO\_THROW\_SIGNATURES|0x0100|関数は関数ポインターとの定義 「は」展開を無効にします。|  
|UNDNAME\_NO\_MEMBER\_TYPE|0x0200|`static` または `virtual` のメンバーの配置を無効にします。|  
|UNDNAME\_NO\_RETURN\_UDT\_MODEL|0x0400|UDT を返すための Microsoft のモデルの配置を無効にします。|  
|UNDNAME\_32\_BIT\_DECODE|0x0800|Undecorates 32 ビットの装飾名。|  
|UNDNAME\_NAME\_ONLY|0x1000|主要な宣言の名前のみを取得します ; の戻り\[範囲\]:: 名前。  テンプレート パラメーターを展開します。|  
|UNDNAME\_TYPE\_ONLY|0x2000|入力は型のエンコーディングです ; 抽象的な宣言を構成します。|  
|UNDNAME\_HAVE\_PARAMETERS|0x4000|実際のテンプレート パラメーターを使用できます。|  
|UNDNAME\_NO\_ECSU|0x8000|列挙と非表示の class\/struct\/union。|  
|UNDNAME\_NO\_IDENT\_CHAR\_CHECK|0x10000|非表示が有効な識別子文字をチェックします。|  
|UNDNAME\_NO\_PTR64|0x20000|出力に ptr64 は含まれません。|  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)