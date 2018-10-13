---
title: 'Ca 1806: メソッドの結果を無視しない |Microsoft Docs'
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
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d28ca688bbad0054f7522034bfe309dcb1fe698
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250108"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: メソッドの結果を無視しない
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 この警告のいくつかの理由があります。  
  
-   新しいオブジェクトが作成されたが、使用されていません。  
  
-   作成して新しい文字列を返すメソッドが呼び出され、新しい文字列が使用されることはありません。  
  
-   HRESULT またはエラー コードを返す COM または P/invoke メソッドは使用されません。 規則の説明  
  
 不要なオブジェクトの作成と使用されていないオブジェクトの関連付けられているガベージ コレクションは、パフォーマンスを低下します。  
  
 文字列は不変であり String.ToUpper などのメソッドが呼び出し元のメソッド内の文字列のインスタンスを変更する代わりに、文字列の新しいインスタンスを返します。  
  
 HRESULT またはエラー コードを無視すると、エラー条件で予期しない動作や低リソース状態が誘導できます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 メソッド A が使用されていません。 B オブジェクトの新しいインスタンスを作成した場合、インスタンスを引数として別のメソッドに渡すまたは変数に代入します。 オブジェクトの作成が必要でない場合は、それを除去- または -  
  
 メソッド A が B、メソッドを呼び出しますが、B メソッドから返される新しい文字列インスタンスを使用しないかどうか。 インスタンスを引数として別のメソッドに渡す、変数に代入します。 または、必要ない場合は、呼び出しを削除します。  
  
 - または -  
  
 またはエラー コードをメソッド A、B のメソッドを呼び出しますが、HRESULT を使用しない場合、メソッドを返します。 条件付きステートメントで、結果を使用して、結果を変数に代入または別のメソッドに引数として渡します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 しない限り、オブジェクトを作成する操作に何らかの目的は、この規則による警告を抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、呼び出し元の String.Trim の結果を無視するクラスを示します。  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->  
  
## <a name="example"></a>例  
 次の例では、String.Trim の結果を元に呼び出された変数に代入を上記の違反を修正します。  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->  
  
## <a name="example"></a>例  
 次の例では、作成したオブジェクトを使用しないメソッドを示します。  
  
> [!NOTE]
>  Visual Basic では、この違反を再現することはできません。  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]  
  
## <a name="example"></a>例  
 次の例は、不要なオブジェクトの作成を削除することで、前の違反を修正します。  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]  
  
## <a name="example"></a>例  
 次の例では、ネイティブ メソッド GetShortPathName から返されるエラー コードを無視するメソッドを示します。  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]  
  
## <a name="example"></a>例  
 次の例では、エラー コードをチェックして、呼び出しが失敗したときに例外がスローされる前の違反を修正します。  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]