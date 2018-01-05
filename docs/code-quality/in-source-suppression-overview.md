---
title: "ソース内抑制の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92babbf3c7a5863d178463b69525bdb722bf28ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="in-source-suppression-overview"></a>ソース内抑制の概要
ソース内抑制を抑制する状況または追加することでマネージ コードでコード分析における規則違反を無視できるは、 **SuppressMessage**属性、違反が発生するコード セグメントをします。 **SuppressMessage**属性には、条件付きコンパイル時に CODE_ANALYSIS コンパイル シンボルが定義されている場合にのみ、マネージ コード アセンブリの IL メタデータに含まれています。  
  
 C + + CLI、ヘッダー ファイルで CA_SUPPRESS_MESSAGE または CA_GLOBAL_SUPPRESS_MESSAGE マクロを使用して、属性を追加します。  
  
 ソース内抑制メタデータを誤って配布を防ぐために、リリース ビルドのソース内抑制を使用する必要がありますできません。 ソース内抑制の処理コストのために、ソース内抑制メタデータを含めることによって、アプリケーションのパフォーマンスを低下する可能性もします。  
  
> [!NOTE]
>  コードがない手動これらの属性自分でします。 詳細については、次を参照してください。[する方法: メニュー項目を使用して警告を抑制する状況](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)です。 メニュー項目では、C++ コードを使用できません。  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage 属性  
 コード分析の警告を右クリックすると、**エラー一覧** をクリックし、**メッセージの抑制**、 **SuppressMessage**属性を追加、コード内、またはに、プロジェクトのグローバル レベルの抑制ファイルです。  
  
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
  
-   **規則のカテゴリ**-ルールが定義されているカテゴリです。 コード分析規則のカテゴリの詳細については、次を参照してください。[マネージ コードの警告のコード分析](../code-quality/code-analysis-for-managed-code-warnings.md)です。  
  
-   **Rule Id** -ルールの識別子。 サポートには、短期および長期のルールの識別子名の両方が含まれます。 短い名前が CAXXXX です。長い名前は、CAXXXX:FriendlyTypeName です。  
  
-   **位置揃え**-テキスト メッセージの抑制の理由を文書化するために使用します。  
  
-   **メッセージ Id** -各メッセージの問題の一意の識別子。  
  
-   **スコープ**-警告を抑制するターゲット。 ターゲットが指定されていない場合は、属性のターゲットに設定されます。 サポートされているスコープ、次のとおりです。  
  
    -   Module  
  
    -   名前空間  
  
    -   リソース  
  
    -   型  
  
    -   メンバー  
  
-   **ターゲット**- 警告を抑制するターゲットを指定するために使用する識別子。 アイテムの完全修飾名でなければなりません。  
  
## <a name="suppressmessage-usage"></a>SuppressMessage の使用方法  
 レベルでコード分析の警告は抑制のインスタンス、 **SuppressMessage**属性を適用します。 これの目的は、違反が発生するコードに抑制情報を密に結合します。  
  
 抑制の一般的な形式には、規則のカテゴリと、ルール名の省略可能な人間が判読できる形式を含むルール識別子が含まれています。 たとえば、オブジェクトに適用された  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 ソース内抑制のメタデータを最小限に抑えるための厳密なパフォーマンス上の理由がある場合は、規則の名前は省略可能です。規則のカテゴリとそのルール ID 一緒に規則を十分に一意の識別子を構成します。 たとえば、オブジェクトに適用された  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 この形式は保守容易性の問題があるため推奨されません。  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>メソッド本体内で複数の違反を抑制します。  
 属性は、メソッドにのみ適用でき、メソッド本体に埋め込むことができません。 ただし、メソッド内で違反の複数の発生を区別するために、メッセージ ID として識別子を指定できます。  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-csharp[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## <a name="generated-code"></a>生成されたコード  
 マネージ コード コンパイラ、および一部のサード パーティ製ツールは、迅速なコードの開発を促進するためのコードを生成します。 ソース ファイルに表示されるコンパイラによって生成されたコードが通常でマークされている、 **GeneratedCodeAttribute**属性。  
  
 コード分析の警告と生成されたコードのエラーを抑制するかどうかを選択できます。 このような警告とエラーを抑制する方法については、次を参照してください。[する方法: 生成されたコードの警告を抑制する状況](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)です。  
  
 コード分析を無視する注**GeneratedCodeAttribute**アセンブリ全体または 1 つのパラメーターのいずれかに適用されたとき。 このような状況はほとんど発生しません。  
  
## <a name="global-level-suppressions"></a>グローバル レベルの抑制  
 マネージ コード分析ツールを調べ**SuppressMessage**アセンブリ、モジュール、型、メンバー、またはパラメーターのレベルで適用される属性です。 違反のリソースと名前空間に対しても適用されます。 これらの違反はグローバル レベルで適用する必要がスコープ設定し、は対象とします。 たとえば、次のメッセージには、名前空間の違反が抑制されます。  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  名前空間スコープで警告を抑制した場合は、それ自体の名前空間に対する警告を抑制します。 名前空間内の型に対する警告は抑制されません。  
  
 任意の抑制は、明示的なスコープを指定することで表現できます。 このような抑制は、グローバル レベルでライブする必要があります。 型を修飾することによって、メンバー レベルの抑制を指定できません。  
  
 グローバル レベルの抑制は、明示的に指定されたユーザーのソースにマップされないコンパイラによって生成されたコードを参照するメッセージを抑制する唯一の方法です。 たとえば、次のコードでは、コンパイラによって生成されたコンス トラクターに対する違反が抑制されます。  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  常に、ターゲットには、アイテムの完全修飾名が含まれています。  
  
## <a name="global-suppression-file"></a>グローバル抑制ファイル  
 グローバル抑制ファイルでは、グローバル レベルの抑制か、ターゲットが指定されていない抑制の抑制を保持します。 たとえば、アセンブリ レベルの違反に対する抑制は、このファイルに格納されます。 また、ASP.NET 抑制は、プロジェクト レベルの設定は、フォームのコードを利用できないために、このファイルに格納されます。 グローバル抑制が作成され、選択した初めてのプロジェクトに追加、**プロジェクト抑制ファイル内**のオプション、**メッセージの抑制**エラー一覧 ウィンドウでコマンド。 詳細については、次を参照してください。[する方法: メニュー項目を使用して警告を抑制する状況](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Diagnostics.CodeAnalysis>