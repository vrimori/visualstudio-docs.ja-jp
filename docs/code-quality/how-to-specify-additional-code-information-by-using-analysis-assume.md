---
title: '方法: _Analysis_assume を使用して追加のコード情報を指定する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 17e25ace1da6cad9fcdc129b6c6f517c39c9c103
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845080"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>方法: _Analysis_assume を使用して追加のコード情報を指定する
C/C++ コード分析のプロセスを支援し、警告を減らすは、コード分析ツールへのヒントを指定できます。 追加情報を提供するには、次の関数を使用します。

 `_Analysis_assume(`  `expr`  `)`

 `expr` -任意の式は true と評価されると見なされます。

 コード分析ツールでは、関数が表示され、式が変更されるまで、たとえば、変数への代入によってが true の時点で、式で表される条件のことを前提としています。

> [!NOTE]
>  `_Analysis_assume` コードの最適化には影響しません。 コード分析ツールでは、外部`_Analysis_assume`操作なしとして定義されます。

## <a name="example"></a>例
 次のコードでは`_Analysis_assume`コード分析の警告を解決する[C6388](../code-quality/c6388.md):

```
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

// calls free and sets ch to null
void FreeAndNull(char* ch);

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

void test( )
{
  char *pc = (char*)malloc(5);
  FreeAndNull(pc);
  _Analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>関連項目
 [__assume](/cpp/intrinsics/assume)