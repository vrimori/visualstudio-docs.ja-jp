---
title: '方法: _analysis_assume を使用してコードを追加情報を指定します |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 608ae6383f95122d5e4b85658b12d454dec24d4e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202541"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>方法: __analysis_assume を使用して追加のコード情報を指定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C/C++ コード分析のプロセスを支援し、警告を減らすは、コード分析ツールへのヒントを指定できます。 追加情報を提供するには、次の関数を使用します。  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -任意の式は true と評価されると見なされます。  
  
 コード分析ツールでは、関数が表示され、式が変更されるまで、たとえば、変数への代入によってが true の時点で、式で表される条件のことを前提としています。  
  
> [!NOTE]
>  `__analysis_assume` コードの最適化には影響しません。 コード分析ツールでは、外部`__analysis_assume`操作なしとして定義されます。  
  
## <a name="example"></a>例  
 次のコードでは`__analysis_assume`コード分析の警告を解決する[C6388](../code-quality/c6388.md):  
  
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
 [__assume](http://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)



