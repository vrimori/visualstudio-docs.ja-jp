---
title: レガシ言語サービス Essentials |Microsoft ドキュメント
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
ms.openlocfilehash: 68b92b821ad77b050ad2116da6fd930b975dad5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135446"
---
# <a name="legacy-language-service-essentials"></a>レガシ言語サービス Essentials
Visual Studio のプログラミング言語に統合する言語サービスを提供する必要があります。 このトピックでは、従来の言語サービスで使用できる機能について説明します。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 言語サービスを実装する新しい方法の詳細についてを参照してください。[エディターおよび言語サービス拡張](../../extensibility/editor-and-language-service-extensions.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
 レガシ言語サービスは、次の機能を提供します。  
  
|機能|説明|  
|-------------|-----------------|  
|構文の色分け表示|さまざまな色と言語のさまざまな要素のフォント スタイルを表示するエディター ビューが発生します。 この区別やすく閲覧、ファイルを編集します。<br /><br /> 一般情報は、次を参照してください。[レガシ言語サービスで構文の色分け](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)です。<br /><br /> Managed package framework (MPF) に、この機能については、次を参照してください。[レガシ言語サービスでの構文が色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)です。|  
|入力候補|ステートメントまたはユーザーが入力を開始したキーワードを完了します。 ステートメント入力候補を使用して、少ない入力とエラーの可能性が少なくなります困難なステートメントをより簡単に入力できます。<br /><br /> 一般情報は、次を参照してください。[レガシ言語サービスで入力候補](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)です。<br /><br /> MPF でこの機能の詳細については、次を参照してください。[レガシ言語サービスでの単語補完](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)です。|  
|中かっこの一致|中かっこなどの文字のペアを強調表示になります。 ときに、ユーザーなどの型終了文字"}"、かっこの照合は、対応する開始文字などが強調表示されます"{"です。 文字を囲むのいくつかのレベルが存在する場合、この機能は、囲み文字の対応が正しいことを確認するユーザーに役立ちます。<br /><br /> MPF でこの機能の詳細については、次を参照してください。[レガシ言語サービスでかっこの照合](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)です。|  
|パラメーター情報ツール ヒント|ユーザーが現在を入力するオーバー ロードされたメソッドに、可能な署名の一覧を表示します。<br /><br /> 一般情報は、次を参照してください。[レガシ言語サービスでのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)です。<br /><br /> MPF でこの機能の詳細については、次を参照してください。[レガシ言語サービスでのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)です。|  
|エラー マーカー|赤い波線の下線とも呼ばれる、波、構文が正しくないテキストの下に表示されます。 エラー マーカーは通常、ユーザーのキーワードのスペルミス、閉じられていないかっこ、無効な文字、および同様のエラーを認識させるのに使用されます。<br /><br /> MPF クラスにエラー マーカーに自動的に処理され、<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>のメソッド、<xref:Microsoft.VisualStudio.Package.AuthoringSink>クラスです。|  
  
 これらの機能の多くには、ソース コードを解析する言語サービスが必要とします。 多くの場合、再利用できる、トークンとコンパイラまたはインタープリターのコードを解析します。  
  
 次の機能は、プログラミング言語のサポートに関連するが、言語サービスの一部ではないです。  
  
|機能|説明|  
|-------------|-----------------|  
|式エバリュエーター|では、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]に表示するブレークポイントを検証し、式のリストを指定することによってデバッガー、 **[自動変数]** デバッグ ウィンドウです。<br /><br /> 詳細については、次を参照してください。[をデバッグ用の言語サービス サポート](../../extensibility/internals/language-service-support-for-debugging.md)です。|  
|シンボル参照のツール|サポート**オブジェクト ブラウザー**、**クラス ビュー**、**呼び出しブラウザー**、および**シンボルの検索結果**です。|