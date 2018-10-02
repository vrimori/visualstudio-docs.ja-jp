---
title: '1725: ca パラメーター名と基本宣言 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 20a7e5f0239d572ec1867ffdac80f116cfd8360a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591966"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: パラメーター名は基本宣言と同一でなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1725: パラメーター名は基本宣言と一致する必要があります](https://docs.microsoft.com/visualstudio/code-quality/ca1725-parameter-names-should-match-base-declaration)します。

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照できるメソッド オーバーライドでのパラメーターの名前は、メソッドの基本宣言またはメソッドのインターフェイス宣言のパラメーターの名前のパラメーターの名前と一致しません。

## <a name="rule-description"></a>規則の説明
 オーバーライド階層のパラメーターに対する一貫性のある名前付けによって、メソッド オーバーライドの有用性が高まります。 派生メソッドのパラメーター名が基本宣言のパラメーター名と異なる場合、メソッドが基本メソッドのオーバーライドであるか、またはメソッドの新しいオーバーライドであるかについて混乱が生じる可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、基本宣言と一致するパラメーターの名前を変更します。 修正プログラムは、COM 参照可能なメソッドの互換性に影響する変更です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 以前に出荷されたライブラリ内の COM 参照可能なメソッドを除き、この規則による警告を抑制しないでください。



