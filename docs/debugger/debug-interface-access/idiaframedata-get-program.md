---
title: "Idiaframedata::get_program |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 10d5d331c4308586485ea77824cda4864c6ee943
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
レジスタの現在の関数呼び出しの前にセットの計算に使用されるプログラム文字列を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]プログラムの文字列を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 プログラムの文字列は、プロローグを確立するために解釈されるマクロのシーケンスです。 たとえば、一般的なスタック フレームを使用プログラム文字列`"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`です。 形式は、逆ポーランド表記法、演算子はオペランドは、次の場所です。 `T0`スタック上の一時変数を表します。 この例では、次の手順を実行します。  
  
1.  レジスタの内容を移動`ebp`に`T0`です。  
  
2.  追加`4`の値に`T0`アドレスが生成、そのアドレスから値を取得、レジスタに値を格納して`eip`です。  
  
3.  格納されているアドレスから値を取得`T0`レジスタに値を格納および`ebp`です。  
  
4.  追加`8`の値に`T0`レジスタに値を格納および`esp`です。  
  
 プログラムの文字列が、CPU と現在のスタック フレームで表される関数を設定する呼び出し規約に固有である注意してください。  
  
## <a name="see-also"></a>参照  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)