---
title: '方法: __analysis_assume を使用して追加のコード情報を指定する'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 50a5daa7080041e6d80f7867888616d2225a1768
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>方法: __analysis_assume を使用して追加のコード情報を指定する
C/C++ コード分析処理に役立つは警告を軽減するため、コード分析ツールへのヒントを提供できます。 追加情報を提供するには、次の関数を使用します。

 `__analysis_assume(`  `expr`  `)`

 `expr` -任意の式を true に評価されると見なされます。

 コード分析ツールでは、式で表される条件は true、関数が表示され、式が変更されるまで、たとえば、変数への代入が true のまま、ポイントではことを前提としています。

> [!NOTE]
>  `__analysis_assume` コードの最適化に影響しません。 コード分析ツールの外部`__analysis_assume`no-op として定義されます。

## <a name="example"></a>例
 次のコードでは`__analysis_assume`コード分析警告を解決する[C6388](../code-quality/c6388.md):

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
  __analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>関連項目
 [__assume](/cpp/intrinsics/assume)