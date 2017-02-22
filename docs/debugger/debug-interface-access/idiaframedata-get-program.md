---
title: "IDiaFrameData::get_program | Microsoft Docs"
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
  - "IDiaFrameData::get_program メソッド"
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

現在の関数を呼び出す前にレジスタ セットを計算するために使用されるプログラムの文字列を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] プログラムの文字列を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` このプロパティをサポートする必要 `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 解説  
 プログラムの文字列はプロローグを確立するために解釈されるマクロのシーケンスです。  たとえば一般的なスタック フレームはプログラムの文字列 `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` を使用する場合があります。  形式は演算子のオペランドを実行して逆記法です。  `T0` はスタックに一時変数を表します。  この例では次の手順が実行されます :  
  
1.  `T0` に登録 `ebp` の内容を移動します。  
  
2.  アドレスを作成するために `4` を `T0` の値に加算しそのアドレスから値を取得しその `eip` レジスタに値を格納します。  
  
3.  値を `T0` に格納されているアドレスから派生し登録 `ebp` にその値を格納します。  
  
4.  `8` を `T0` の値に加算し登録 `esp` にその値を格納します。  
  
 プログラムの文字列が CPU と現在のスタック フレームで表される関数の呼び出し規約の設定に固有であることに注意してください。  
  
## 参照  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)