---
title: ソース内抑制の概要 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7f02a57be8d267126deb6736c9e0a690b1ac3e2d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540320"
---
# <a name="in-source-suppression-overview"></a>ソース内抑制の概要
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ソース内抑制の概要](https://docs.microsoft.com/visualstudio/code-quality/in-source-suppression-overview)します。  
  
ソース内抑制は非表示または追加することでマネージ コードでコード分析の違反を無視する機能、 **SuppressMessage**属性を違反が発生するコードのセグメント。 **SuppressMessage** CODE_ANALYSIS コンパイルのシンボルがコンパイル時に定義されている場合にのみ、マネージ コード アセンブリの IL メタデータに含まれている条件付き属性です。  
  
 C++/cli、CLI、ヘッダー ファイルの属性を追加する CA_SUPPRESS_MESSAGE または CA_GLOBAL_SUPPRESS_MESSAGE マクロを使用します。  
  
 ソース内抑制のメタデータを誤って発送を防ぐために、リリース ビルドのソース内抑制を使用する必要がありますできません。 ソース内抑制の処理コスト、ために、ソース内抑制のメタデータを含めることによって、アプリケーションのパフォーマンスを低下する可能性もします。  
  
> [!NOTE]
>  コードがない渡すためにこれらの属性自分でします。 詳細については、次を参照してください。[方法: メニュー項目を使用して警告を抑制する](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)します。 メニュー項目は、C++ コードのご利用いただけません。  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage 属性  
 コード分析警告を右クリックすると、**エラー一覧**順にクリックします**メッセージの抑制**、 **SuppressMessage**属性が、コード内、またはに追加しますプロジェクトのグローバル抑制ファイルです。  
  
 **SuppressMessage**属性は、次の形式。  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```csharp  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 [C++]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 この場合、  
  
-   **ルール カテゴリ**-ルールが定義されているカテゴリ。 コード分析ルールのカテゴリの詳細については、次を参照してください。[マネージ コードの警告のコード分析](../code-quality/code-analysis-for-managed-code-warnings.md)します。  
  
-   **規則 Id** -ルールの識別子。 サポートには、短期および長期のルールの識別子名の両方が含まれます。 短い名前が CAXXXX;長い名前は、CAXXXX:FriendlyTypeName です。  
  
-   **位置揃え**-メッセージの抑制の理由を文書化に使用されるテキスト。  
  
-   **メッセージ Id** -各メッセージの問題の一意識別子。  
  
-   **スコープ**-警告を抑制するターゲット。 ターゲットが指定されていない場合は、属性のターゲットに設定されます。 サポートされているスコープを以下に示します。  
  
    -   Module  
  
    -   名前空間  
  
    -   リソース  
  
    -   型  
  
    -   メンバー  
  
-   **ターゲット**- 警告を抑制するターゲットを指定するために使用する識別子。 項目の完全修飾名を含める必要があります。  
  
## <a name="suppressmessage-usage"></a>SuppressMessage 使用状況  
 先のレベルでコード分析の警告を抑制のインスタンス、 **SuppressMessage**属性を適用します。 この目的は、違反が発生する抑制については、コードに密に結合します。  
  
 抑制の一般的な形式には、ルールのカテゴリと、ルール名の省略可能な人間が判読できる形式を格納しているルール識別子が含まれています。 たとえば、オブジェクトに適用された  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 ソース内抑制のメタデータを最小限に抑えるための厳密なパフォーマンス上の理由がある場合は、規則の名前を省略しても構いません。ルール カテゴリとそのルールの ID 構成規則を十分に一意の識別子。 たとえば、オブジェクトに適用された  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 この形式は保守容易性の問題があるため推奨されません。  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>メソッド本体内で複数の違反を抑制します。  
 属性は、メソッドにのみ適用でき、メソッド本文内に埋め込むことはできません。 ただし、複数回出現メソッド内での違反を区別するために、メッセージの ID として識別子を指定できます。  
  
 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]  
  
## <a name="generated-code"></a>生成されたコード  
 マネージ コード コンパイラと一部のサード パーティ製ツールは、迅速なコードの開発を促進するためのコードを生成します。 ソース ファイルに表示されるコンパイラによって生成されたコードがでマークされたは、通常、 **GeneratedCodeAttribute**属性。  
  
 コード分析の警告と生成されたコードのエラーを抑制するかどうかを選択できます。 このような警告とエラーを抑制する方法については、次を参照してください。[方法: 生成されたコードの警告を抑制する](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)します。  
  
 コード分析を無視する注**GeneratedCodeAttribute**アセンブリ全体または 1 つのパラメーターのいずれかに適用されます。 このような状況はほとんど発生しません。  
  
## <a name="global-level-suppressions"></a>グローバル レベルの抑制  
 マネージ コード分析ツールを検査**SuppressMessage**アセンブリ、モジュール、型、メンバー、またはパラメーターのレベルで適用される属性。 リソースと名前空間に対する違反が発生します。 これらの違反、グローバル レベルで適用する必要がありますスコープし、は対象とします。 たとえば、次のメッセージには、名前空間の違反が抑制されます。  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  名前空間スコープで警告を抑制すると、名前空間自体に対して警告を抑制します。 名前空間内の型に対する警告は抑制されません。  
  
 任意の抑制は、明示的なスコープを指定することによって表現できます。 このような抑制は、グローバル レベルでライブする必要があります。 メンバー レベルの抑制は、型を修飾して指定できません。  
  
 グローバル レベルの抑制は、明示的に指定されたユーザーのソースにマップされていないコンパイラによって生成されたコードを参照するメッセージを抑制する唯一の方法です。 たとえば、次のコードでは、コンパイラによって生成されたコンス トラクターに対する違反が抑制されます。  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  常に、ターゲットには、項目の完全修飾名が含まれています。  
  
## <a name="global-suppression-file"></a>グローバル抑制ファイル  
 グローバル抑制はグローバル レベルの抑制またはターゲットが指定されていない抑制の抑制が保持されます。 たとえば、アセンブリ レベルの違反の抑制は、このファイルに格納されます。 さらに、いくつかの ASP.NET の抑制は、プロジェクト レベルの設定は、フォームのコードを利用できないために、このファイルに格納されます。 グローバル抑制は作成され、選択した初めてのプロジェクトに追加、**プロジェクト抑制ファイル内**のオプション、**メッセージの抑制**エラー一覧 ウィンドウでコマンド。 詳細については、次を参照してください。[方法: メニュー項目を使用して警告を抑制する](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Diagnostics.CodeAnalysis>



