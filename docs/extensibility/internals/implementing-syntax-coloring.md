---
title: 構文の色分けを実装する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5502bd30378130e5977d427acb9df5b73226a05b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-syntax-coloring"></a>構文の色分けを実装します。
言語サービスは、構文の色表示機能を提供する場合、パーサーは、行のテキスト装飾が可能な項目の配列に変換し、これらの装飾が可能な項目に対応するトークンの種類を返します。 パーサーは、装飾が可能な項目の一覧に属しているトークンの種類を返す必要があります。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 適切なトークンの種類に colorizer オブジェクトによって割り当てられた属性に従ってコード ウィンドウで各装飾が可能な項目を表示します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] パーサー インターフェイスが指定されていませんし、パーサーの実装が決定できます。 ただし、既定のパーサー実装は、言語の Visual Studio パッケージ プロジェクトで提供されます。 マネージ コードの場合は、マネージ パッケージ フレームワーク (MPF) は、テキストを色分け完全にサポートを提供します。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 構文の色分けを実装する新しい方法の詳細についてを参照してください。[チュートリアル: テキストを強調表示](../../extensibility/walkthrough-highlighting-text.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>テキストの色分けにエディターでの手順  
  
1.  エディターを呼び出して、colorizer の取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>オブジェクト。  
  
2.  エディターの呼び出し、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> colorizer に、colorizer 外に維持するには、各ラインの状態が必要かどうかを調べます。  
  
3.  エディターを呼び出す、colorizer では、状態を colorizer 外維持する必要がある場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>最初の行の状態を取得します。  
  
4.  エディターを呼び出し、バッファー内の各行の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッドで、次の手順を実行します。  
  
    1.  テキストの行は、テキストをトークンに変換するスキャナーに渡されます。 各トークンは、トークンのテキストとトークンの種類を指定します。  
  
    2.  トークン型は、装飾が可能な項目の一覧へのインデックスに変換されます。  
  
    3.  トークンの情報は、配列、配列の各要素は、行の文字に対応するようを埋めるために使用されます。 配列に格納された値は、装飾が可能な項目の一覧にインデックスです。  
  
    4.  行ごとに、行の末尾に状態が返されます。  
  
5.  Colorizer では、状態を維持する必要がある場合、エディターは、その行の状態をキャッシュします。  
  
6.  エディターから返される情報を使用してテキストの行を表示する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッドです。 この場合、次の手順が必要です。  
  
    1.  行の各文字の装飾が可能な項目のインデックスを取得します。  
  
    2.  既定の装飾が可能な項目を使用する場合、エディターの装飾が可能な項目の一覧にアクセスします。  
  
    3.  それ以外の場合、呼び出す言語サービスの<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>装飾が可能な項目を取得します。  
  
    4.  装飾が可能な項目の表示にテキストを表示するために情報を使用します。  
  
## <a name="managed-package-framework-colorizer"></a>Managed Package Framework Colorizer  
 Managed package framework (MPF) は、colorizer を実装するために必要なすべてのクラスを提供します。 言語サービス クラスを継承する必要があります、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスし、必要なメソッドを実装します。 実装することで、スキャナーとパーサーを指定する必要があります、<xref:Microsoft.VisualStudio.Package.IScanner>インターフェイス、およびそのインターフェイスからのインスタンスを返す、<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>メソッド (のいずれかで実装する必要がある、<xref:Microsoft.VisualStudio.Package.LanguageService>クラス)。 詳細については、次を参照してください。[レガシ言語サービスでの構文が色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: 組み込みの装飾が可能な項目を使用して](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [カスタムの装飾が可能な項目](../../extensibility/internals/custom-colorable-items.md)   
 [レガシ言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [従来の言語サービスでの構文の配色変更](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)