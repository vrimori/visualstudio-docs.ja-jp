---
title: "ビルド確認テストのコード カバレッジの分析 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: 8
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 351ec5b60e84ed1633c26751173a4b7e4af663dd
ms.contentlocale: ja-jp
ms.lasthandoff: 05/13/2017

---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>ビルド確認テストのコード カバレッジの分析
Microsoft Visual Studio のコード カバレッジ分析は、コードの中で自動テストで実行されている割合を示します。 詳細については、「[コード カバレッジを使用した、テストされるプロジェクトのコード割合の確認](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)」を参照してください。  
  
 コードをチェックインすると、テストがビルド サーバー上で、他のチーム メンバーによる他のすべてのテストと共に実行されます。 まだこの設定を行っていない場合は、「[ビルド プロセスでのテストの実行](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38)」を参照してください。これによって、プロジェクト全体のカバレッジに関する最新の全体像が提供されるため、ビルド サービスのコード カバレッジを分析する場合に便利です。 これには、自動化されたシステム テストと、通常は開発用コンピューターでは実行しない、その他のコード化されたテストも含まれます。  
  
1.  チーム エクスプローラーで、[**ビルド**] を開き、ビルド定義を追加または編集します。  
  
2.  [**プロセス**] ページで [**自動テスト**]、[**テスト ソース**]、[**実行設定**] の順に展開します。 [**実行設定の種類**] を [**コード カバレッジの有効化**] に設定します。  
  
     複数のテスト ソース定義がある場合は、各定義に対してこの手順を繰り返します。  
  
    -   *ただし、**[実行設定の種類]** というフィールドはありません。*  
  
         [**自動テスト**] の下の [**テスト アセンブリ**] を選択し、行の末尾の省略記号 (**[...]**) ボタンを選択します。 [**テストの実行の追加と編集**] ダイアログ ボックスで、[**テスト ランナー**] の下の [**Visual Studio テスト ランナー**] を選択します。  
  
 ![コード カバレッジのビルド定義の設定](../test/media/codecoverage-plaincc.png "CodeCoverage-plainCC")  
  
 ビルドの実行後、コード カバレッジの結果がビルドの概要に表示されます。  
  
## <a name="see-also"></a>関連項目  
 [コード カバレッジを使用した、テストされるプロジェクトのコード割合の確認](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

