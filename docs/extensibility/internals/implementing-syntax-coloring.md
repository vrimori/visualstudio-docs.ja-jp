---
title: 構文の色分けを実装する |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de1a73cda8be9e56b0cad605f5507d52509ec906
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038046"
---
# <a name="implementing-syntax-coloring"></a>構文の色分け表示の実装
言語サービスでは、構文の色表示機能を提供して、パーサー配色可能な項目の配列に 1 行のテキストを変換します。 これらの装飾が可能な項目に対応するトークンの種類を返します。 パーサーは、装飾が可能な項目の一覧に属するトークンの型を返す必要があります。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] colorizer オブジェクトによって適切なトークンの種類に割り当てられた属性に基づいて、コード ウィンドウ内の各装飾が可能な項目を表示します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] パーサーのインターフェイスを指定しないおよびパーサーの実装が完全にユーザーが決定できます。 ただし、既定のパーサーの実装は、Visual Studio 言語パッケージ プロジェクトで提供されます。 マネージ コード用 managed package framework (MPF) のテキストを色分け、完全なサポートが提供します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 構文の色分けを実装する新しい方法の詳細についてを参照してください。[チュートリアル。テキストの強調表示](../../extensibility/walkthrough-highlighting-text.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>テキストを色分けして表示するエディターで実行する手順  
  
1.  エディターを呼び出して、colorizer の取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>オブジェクト。  
  
2.  エディターの呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>メソッド、colorizer のニーズ、colorizer の外部に保持するには、各回線の状態かどうかを決定します。  
  
3.  エディターを呼び出す、colorizer は、状態を colorizer の外部に保持する必要がある場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>最初の行の状態を取得します。  
  
4.  エディターを呼び出し、バッファー内の各行に対して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッドで、次の手順を実行します。  
  
    1.  行のテキストは、テキストをトークンに変換するスキャナーに渡されます。 各トークンは、トークンのテキストとトークンの種類を指定します。  
  
    2.  トークン型は、装飾が可能な項目の一覧へのインデックスに変換されます。  
  
    3.  トークンの情報は、配列、配列の各要素は、行の文字に対応するようを埋めるために使用されます。 配列に格納されている値は、装飾が可能な項目の一覧にインデックスです。  
  
    4.  各行の行の最後に状態が返されます。  
  
5.  Colorizer では、状態を維持する必要がある場合、エディターは、その行の状態をキャッシュします。  
  
6.  エディターから返される情報を使用してテキストの行を表示する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッド。 この場合、次の手順が必要です。  
  
    1.  行内の各文字の装飾が可能な項目のインデックスを取得します。  
  
    2.  既定の配色可能な項目を使用して場合エディターの配色可能な項目の一覧にアクセスします。  
  
    3.  それ以外の場合、言語サービスを呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>装飾が可能な項目を取得します。  
  
    4.  画面にテキストを表示するために、装飾が可能な項目の情報を使用します。  
  
## <a name="managed-package-framework-colorizer"></a>Managed Package Framework Colorizer  
 Managed package framework (MPF) は、colorizer を実装するために必要なすべてのクラスを提供します。 言語サービス クラスを継承する必要があります、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスし、必要なメソッドを実装します。 スキャナーとパーサーを実装することで指定する必要があります、<xref:Microsoft.VisualStudio.Package.IScanner>インターフェイスし、そのインターフェイスからのインスタンスを返す、<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>メソッド (いずれの方法で実装する必要があります、<xref:Microsoft.VisualStudio.Package.LanguageService>クラス)。 詳細については、次を参照してください。[従来の言語サービスでの構文の色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)します。  
  
## <a name="see-also"></a>関連項目  
 [方法: 組み込みの配色可能な項目を使用して、](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [カスタムの配色可能な項目](../../extensibility/internals/custom-colorable-items.md)   
 [従来の言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [従来の言語サービスでの構文の配色変更](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)