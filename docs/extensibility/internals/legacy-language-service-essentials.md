---
title: "従来の言語サービス Essentials |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f6f8ba46289e27b2465436a103091983c17de1c0
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-language-service-essentials"></a>従来の言語サービスの基礎
Visual Studio プログラミング言語に統合する言語サービスを提供する必要があります。 このトピックでは、従来の言語サービスで利用できる機能について説明します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 言語サービスを実装する新しい方法の詳細については、次を参照してください。[エディターおよび言語拡張機能をサービス](../../extensibility/editor-and-language-service-extensions.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
 従来の言語サービスは、次の機能を提供します。  
  
|特性|説明|  
|-------------|-----------------|  
|構文の色分け表示|別の色と言語のさまざまな要素のフォント スタイルを表示する [エディター] ビューをさせます。 この区別によりように読みやすさとファイルを編集します。<br /><br /> 一般情報は、次を参照してください。[レガシ言語サービスで構文の色分け](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)します。<br /><br /> マネージ パッケージ フレームワーク (MPF) では、この機能の詳細については、次を参照してください。[レガシ言語サービスでの構文の色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)します。|  
|ステートメント入力候補|ステートメントまたはユーザーが入力を開始したキーワードを完了します。 ステートメント入力候補により、ユーザーがより簡単に少量の入力、エラーの少ない可能性と困難なステートメントを入力します。<br /><br /> 一般情報は、次を参照してください。[レガシ言語サービスでのステートメント入力候補](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)します。<br /><br /> MPF でこの機能の詳細については、次を参照してください。[レガシ言語サービスで単語補完](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)します。|  
|中かっこの一致|中かっこなどの文字のペアを強調表示になります。 ユーザーが終了文字など、"}"、かっこの一致には、対応する開始文字をなどが強調表示"{"です。 文字を囲むのいくつかのレベルが存在する場合、この機能は囲み文字の対応が正しいことを確認するユーザーに役立ちます。<br /><br /> MPF でこの機能の詳細については、次を参照してください。[レガシ言語サービスでかっこの一致](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)します。|  
|パラメーター情報のツールヒント|オーバー ロードされたメソッド、ユーザーが入力して現在の可能なシグネチャの一覧を表示します。<br /><br /> 一般情報は、次を参照してください。[レガシ言語サービスでパラメーター情報](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)します。<br /><br /> MPF でこの機能の詳細については、次を参照してください。[レガシ言語サービスでパラメーター情報](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)します。|  
|エラー マーカー|赤い波線の下線とも呼ばれる、波、構文が正しくないテキストの下に表示されます。 エラー マーカー通常使用すると、ユーザーのキーワードのスペルミス、閉じられていないかっこ、無効な文字のようなエラーに注意してください。<br /><br /> MPF クラスでエラー マーカーが<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A><xref:Microsoft.VisualStudio.Package.AuthoringSink>クラス</xref:Microsoft.VisualStudio.Package.AuthoringSink>のメソッド</xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>の処理に自動的に|  
  
 これらの機能の多くには、ソース コードを解析する言語サービスが必要とします。 多くの場合、再利用できるトークン化して、コンパイラやインタープリターのコードを解析します。  
  
 次の機能は、プログラミング言語をサポートするためのものが、言語サービスの一部ではないです。  
  
|特性|説明|  
|-------------|-----------------|  
|式エバリュエーター|サポート、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ブレークポイントを検証し、式のリストを指定することによってデバッガーに表示されますが、 **[自動変数]**デバッグ ウィンドウ。<br /><br /> 詳細については、次を参照してください。[をデバッグ用の言語サービス サポート](../../extensibility/internals/language-service-support-for-debugging.md)します。|  
|シンボル参照のツール|サポート**オブジェクト ブラウザー**、**クラス ビュー**、**呼び出しブラウザー**、および**シンボルの検索結果**します。|
