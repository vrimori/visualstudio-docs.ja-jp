---
title: コード分析のアプリケーション エラー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 66d611903c71cc526c01c1062c85ceef2e7975f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225018"
---
# <a name="code-analysis-application-errors"></a>コード分析のアプリケーション エラー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
このセクションでは、マネージ コード分析ツールによって生成されるエラー メッセージの参照です。 に特定のエラー メッセージのヘルプを取得するには、でのエラー番号を入力、**探して**キーワードします。

## <a name="in-this-section"></a>このセクションの内容

|||
|-|-|
|[CA0001](ca0001.md)|予期されるエラー状態を示さないマネージ コード分析ツール内で例外が発生しました。|
|[CA0051](ca0051.md)|規則が選択されていません。|
|[CA0052](ca0052.md)|分析するターゲットが選択されていません。|
|[CA0053](ca0053.md)|規則アセンブリを読み込むことができませんでした。|
|[CA0054](ca0054.md)|カスタム ルール アセンブリが無効な XML リソースです。|
|[CA0055](ca0055.md)|ファイルを読み込むことができません:\<パス >|
|[CA0056](ca0056.md)|プロジェクト ファイルは、分析ツールの正しくないバージョンです。|
|[CA0057](ca0057.md)|違反は、ターゲットおよびルールの現在のセットにマップすることはできません。|
|[CA0058](ca0058.md)|参照されるアセンブリを読み込めません。|
|[CA0059](ca0059.md)|コマンド ライン スイッチのエラー。|
|[CA0060](ca0060.md)|間接的に参照アセンブリを読み込めません。|
|[CA0061](ca0061.md)|ルール '*RuleId*' は見つかりませんでした。|
|[CA0062](ca0062.md)|ルール '*RuleId*'規則セットで参照されている'*RuleSetName*' は見つかりませんでした。|
|[CA0063](ca0063.md)|規則セット ファイルまたはその依存ルール セット ファイルのいずれかの読み込みに失敗しました。|
|[CA0064](ca0064.md)|指定された規則セットに FxCop ルールが含まれていないために、分析は実行されません。|
|[CA0065](ca0065.md)|サポートされていないメタデータ構造: 型 '*TypeName*'プロパティと同じ名前のフィールドの両方を含む'*PropertyFieldName*'|
|[CA0066](ca0066.md)|値 '*VersionID*' に提供される、 **/targetframeworkversion**認識されているバージョンではありません。|
|[CA0067](ca0067.md)|ディレクトリが見つかりません。|
|[CA0068](ca0068.md)|デバッグ ターゲット アセンブリの情報が見つかりませんでした *'AssemblyName'* します。|
|[CA0069](ca0069.md)|別のプラットフォームを使用します。 *FrameworkVersion1*は見つかりませんでした。 使用して*FrameworkVersion2*代わりにします。 最良の分析結果は、適切な .NET Framework がインストールされていることを確認してください。|
|[CA0070](ca0070.md)|アセンブリまたはセキュリティのアクセス許可のための型を読み込むことができません。|
|[CA0501](ca0501.md)|レポート出力を読み取ることができません。|
|[CA0502](ca0502.md)|サポートされていない言語です。|
|[CA0503](ca0503.md))|プロパティは、推奨されていません。 優先するプロパティを使用します。|
|[CA0504](ca0504.md)|存在しないために、ルールのディレクトリは無視されました|
|[CA0505](ca0505.md)|プロパティは、推奨されていません。 優先するプロパティを使用します。|
|[FxCopCmd エラー](fxcopcmd-errors.md)|マネージ コード分析エラー。|
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|コード分析チェックイン ポリシー エラーです。|

## <a name="related-sections"></a>関連項目

- [セキュリティで保護されたコードの記述に関するガイドライン](http://msdn.microsoft.com/en-us/9892fd19-45cd-44b6-9fa8-10f1b5cb6ea4)
- [マネージド コードの品質の分析](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [アプリケーション ライフ サイクル管理ツールのエラーのトラブルシューティングに関するリソース](http://msdn.microsoft.com/library/76ca8f76-1e2d-4b55-89e2-bd59e4abe74c)