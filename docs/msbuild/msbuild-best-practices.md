---
title: "MSBuild ベスト プラクティス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3c2a1e55c9a43a8e94ed577fc8de135d76e12da5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
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
