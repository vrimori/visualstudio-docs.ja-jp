---
title: "MSBuild ベスト プラクティス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: a48867456cd6ac60c5fc6ca53fcadbc4ad787711
ms.contentlocale: ja-jp
ms.lasthandoff: 08/14/2017

---
# <a name="msbuild-best-practices"></a>MSBuild のベスト プラクティス
MSBuild スクリプトを記述するための次のベスト プラクティスを推奨します。  
  
-   既定のプロパティ値は、コマンド ラインで既定値をオーバーライドできるプロパティを宣言するのではなく、`Condition` 属性を使用して処理することをお勧めします。 たとえば、次を使用します。  
  
     `<MyProperty Condition="'$(MyProperty)' == ''">`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   項目を選択するときに、ワイルドカードを避けます。 代わりに、ファイルを明示的に指定します。 ファイルを追加または削除する場合に発生する可能性のあるエラーを追跡しやすくなります。  
  
## <a name="see-also"></a>関連項目  
 [詳細な概念](../msbuild/msbuild-advanced-concepts.md)

