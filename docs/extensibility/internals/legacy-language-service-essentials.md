---
title: 従来の言語サービスの基本情報 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 344a7949c5058237d8599d69ea3b234e9a6e8e72
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850178"
---
# <a name="legacy-language-service-essentials"></a>従来の言語サービスの基本情報
Visual Studio のプログラミング言語に統合する言語サービスを提供する必要があります。 このトピックでは、従来の言語サービスで使用できる機能について説明します。  

 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 言語サービスを実装する新しい方法の詳細についてを参照してください。[エディターと言語サービス拡張](../../extensibility/editor-and-language-service-extensions.md)します。  

> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  

 従来の言語サービスでは、次の機能を提供します。  

|機能|説明|  
|-------------|-----------------|  
|構文の色分け表示|により、エディター ビューは、さまざまな色と言語のさまざまな要素のフォント スタイルを表示します。 この区別により作成の読み取りし、ファイルを編集しやすくします。<br /><br /> 一般的な情報は、次を参照してください。[従来の言語サービスでの構文の色分け表示](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)します。<br /><br /> Managed package framework (MPF) でこの機能については、次を参照してください。[従来の言語サービスでの構文の色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)します。|  
|入力候補|ステートメントまたはユーザーが入力を開始したキーワードを完了します。 ステートメント入力候補を使用して、少ない入力、エラーが少ない可能性と困難なステートメントをより簡単に入力できます。<br /><br /> 一般的な情報は、次を参照してください。[従来の言語サービスで入力候補](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)します。<br /><br /> MPF でこの機能については、次を参照してください。[従来の言語サービスでの単語補完](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)します。|  
|かっこの一致|中かっこなどの文字のペアを強調表示になります。 ユーザーが終了文字など"}"、かっこの一致を強調表示、対応するなどの文字を開く"{0}"。 文字を囲むのいくつかのレベルが存在する場合、この機能は、囲み文字の対応が正しいことを確認します。 ユーザーに役立ちます。<br /><br /> MPF でこの機能については、次を参照してください。[従来の言語サービスでかっこの照合](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)します。|  
|パラメーター情報のヒント|オーバー ロードされたメソッド、ユーザーの現在の入力の可能な署名の一覧が表示されます。<br /><br /> 一般的な情報は、次を参照してください。[従来の言語サービスでのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)します。<br /><br /> MPF でこの機能については、次を参照してください。[従来の言語サービスでのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)します。|  
|エラーのマーカー|赤い波線の下線とも呼ばれる、波線、構文が正しくないテキストの下に表示されます。 通常、エラー マーカーは、ユーザーのキーワードのスペルミス、閉じられていないかっこ、無効な文字、および同様のエラーを認識させるのに使用されます。<br /><br /> MPF クラスでエラーのマーカーが自動的に処理、<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>のメソッド、<xref:Microsoft.VisualStudio.Package.AuthoringSink>クラス。|  

 これらの機能の多くには、ソース コードを解析する言語サービスが必要です。 多くの場合、再利用できますトークン化して、コンパイラやインタープリター用のコードを解析します。  

 次の機能は、関連するプログラミング言語のサポートが言語サービスの一部ではないです。  


| 機能 | 説明 |
|-----------------------| - |
| 式エバリュエーター | では、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]に表示されるデバッガーのブレークポイントの検証の式のリストを指定して、 **[自動変数]** デバッグ ウィンドウ。<br /><br /> 詳細については、次を参照してください。[をデバッグ用の言語サービスのサポート](../../extensibility/internals/language-service-support-for-debugging.md)します。 |
| シンボル参照ツール | サポート**オブジェクト ブラウザー**、**クラス ビュー**、**呼び出しブラウザー**、および**シンボルの検索結果**します。 |

