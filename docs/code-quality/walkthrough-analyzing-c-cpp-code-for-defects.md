---
title: 'チュートリアル : C/C++ コード分析による障害の検出'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 60cdc07b35480509152fd09fefb484557358fba0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>チュートリアル : C/C++ コード分析による障害の検出

このチュートリアルでは、コードと C/C++ コードのコード分析ツールを使用して潜在的なコードの不具合のコードと C/C++ コードを分析する方法を示します。

- ネイティブ コードに対してコード分析を実行します。
- コード障害の警告を分析します。
- 警告をエラーとして扱うです。
- コード障害の分析を向上させるためにソース コードの注釈を設定します。

## <a name="prerequisites"></a>必須コンポーネント

- コピー、[デモ サンプル](../code-quality/demo-sample.md)です。
- C と C++ の基本を理解します。

### <a name="to-run-code-defect-analysis-on-native-code"></a>ネイティブ コードに対してコード障害の分析を実行するには

1. デモ ソリューションを開いて[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。

     デモのソリューションを今すぐ設定**ソリューション エクスプ ローラー**です。

2. **ビルド** メニューのをクリックして**ソリューションのリビルド**です。

     ソリューションは、エラーまたは警告なしでビルドします。

3. **ソリューション エクスプ ローラー**、CodeDefects プロジェクトを選択します。

4. **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

     **プロパティ ページの [CodeDefects** ] ダイアログ ボックスが表示されます。

5. をクリックして**コード分析**です。

6. クリックして、**ビルド時に C/C++ のコード分析を有効にする**チェック ボックスをオンします。

7. CodeDefects プロジェクトをリビルドします。

     コード分析の警告が表示されます、**エラー一覧**です。

### <a name="to-analyze-code-defect-warnings"></a>コード障害の警告を分析するには

1. **ビュー**  メニューのをクリックして**エラー一覧**です。

     選択した開発者プロファイルに応じて[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、 をポイントする必要があります**その他のウィンドウ**上、**ビュー**  メニューをクリックして**エラー一覧**です。

2. **エラー一覧**、次の警告をダブルクリックします。

     警告 C6230: 意味の異なる型の間の暗黙的なキャスト: HRESULT をブール値のコンテキストを使用します。

     コード エディターには、関数で、警告の原因となった行が表示されます。`bool``ProcessDomain()`です。 この警告は、HRESULT が使用されている 'if' ステートメントにブール型の結果が必要な場所を示します。

3. SUCCEEDED マクロを使用してこの警告を解決します。 コードは、次のコードのようになります。

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. **エラー一覧**、次の警告をダブルクリックします。

     警告 C6282: 不適切な演算子: テストのコンテキストの定数を代入します。 「= = を意図したものですか。

5. 等しいかどうかをテストして、この警告を解決します。 コードは、次のコードのようになります。

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>警告をエラーとして扱うには

1. 次のコードを追加、Bug.cpp ファイル`#pragma`C6001 警告をエラーとして処理するファイルの先頭にステートメント。

   ```cpp
   #pragma warning (error: 6001)
   ```

2. CodeDefects プロジェクトをリビルドします。

     **エラー一覧**C6001 がエラーとして表示されます。

3. 残りの 2 つ C6001 エラーを修正、**エラー一覧**初期化することによって`i`と`j`を 0 にします。

4. CodeDefects プロジェクトをリビルドします。

     警告またはエラーを行わなくても、プロジェクトをビルドします。

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Annotation.c でソース コード注釈の警告を解決するには

1. ソリューション エクスプ ローラーで、注釈プロジェクトを選択します。

2. **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

     **注釈プロパティ ページ** ダイアログ ボックスが表示されます。

3. をクリックして**コード分析**です。

4. 選択、**ビルド時に C/C++ のコード分析を有効にする**チェック ボックスをオンします。

5. 注釈のプロジェクトを再構築します。

6. **エラー一覧**、次の警告をダブルクリックします。

     警告 C6011: NULL ポインター 'newNode' を逆参照します。

     この警告は、戻り値をチェックする、呼び出し元がエラーを示します。 この場合は、呼び出しで**AllocateNode** NULL 値を返す可能性があります (AllocateNode の関数宣言の annotations.h ヘッダー ファイルを参照してください)。

7. Annotations.cpp ファイルを開きます。

8. この警告を解決するには、'if' ステートメントを使用して、戻り値をテストします。 コードは、次のコードのようになります。

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. 注釈のプロジェクトを再構築します。

     警告またはエラーを行わなくても、プロジェクトをビルドします。

### <a name="to-use-source-code-annotation"></a>ソース コードの注釈を使用するには

1. 関数の戻り値の仮パラメーターの注釈設定と`AddTail`プレおよびポストトリガーは条件でこの例で示すようにします。

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. 注釈のプロジェクトをリビルドします。

3. **エラー一覧**、次の警告をダブルクリックします。

     警告 C6011: NULL ポインター 'node' を逆参照します。

     この警告は、関数に渡されたノードが、null であることを示し、警告が発生した行番号を示します。

4. この警告を解決するには、'if' ステートメントを使用して、戻り値をテストします。 コードは、次のコードのようになります。

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. 注釈のプロジェクトをリビルドします。

     警告またはエラーを行わなくても、プロジェクトをビルドします。

## <a name="see-also"></a>関連項目

[チュートリアル: マネージ コードを分析するコードの不具合の](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[c/c++ コード分析](../code-quality/code-analysis-for-c-cpp-overview.md)