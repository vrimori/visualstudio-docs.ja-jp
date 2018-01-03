---
title: "MSBuild ベスト プラクティス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9634fe1a0fa26d5180edc9312b925e6740bac216
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
