---
title: MSBuild ベスト プラクティス | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2572e300c666462c5f514452a40f810a349040f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild-best-practices"></a>MSBuild のベスト プラクティス
MSBuild スクリプトを記述するための次のベスト プラクティスを推奨します。  
  
-   既定のプロパティ値は、コマンド ラインで既定値をオーバーライドできるプロパティを宣言するのではなく、`Condition` 属性を使用して処理することをお勧めします。 たとえば、次を使用します。  
  
     `<MyProperty Condition="'$(MyProperty)' == ''">`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   項目を選択するときに、ワイルドカードを避けます。 代わりに、ファイルを明示的に指定します。 ファイルを追加または削除する場合に発生する可能性のあるエラーを追跡しやすくなります。  
  
## <a name="see-also"></a>参照  
 [詳細な概念](../msbuild/msbuild-advanced-concepts.md)
