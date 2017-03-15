---
title: "ソース内抑制の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソースの抑制, コード分析"
  - "コード分析, ソースの抑制"
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 40
---
# ソース内抑制の概要
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ソース内抑制とは、違反の原因になっているコード セグメントに **SuppressMessage** 属性を追加して、マネージ コードでコード分析における規則違反を抑制または無視する機能です。  **SuppressMessage** 属性は条件属性であり、コンパイル時にコンパイル シンボル CODE\_ANALYSIS を定義した場合のみマネージ コード アセンブリの IL メタデータに含められます。  
  
 C\+\+\/CLI では、属性を追加するには、ヘッダー ファイルで CA\_SUPPRESS\_MESSAGE マクロまたは CA\_GLOBAL\_SUPPRESS\_MESSAGE マクロを使用します。  
  
 ソース内抑制のメタデータが誤って出荷されることがないように、リリース ビルドではソース内抑制を使わないようにしてください。  ソース内抑制の処理負荷のため、ソース内抑制のメタデータを含めるとアプリケーションのパフォーマンスが低下する可能性もあります。  
  
> [!NOTE]
>  これらの属性をハンド コードする必要はありません。  詳細については、「[方法: メニュー項目を使用して警告を抑制する](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)」を参照してください。  C\+\+ コードではメニュー項目を使用できません。  
  
## SuppressMessage 属性  
 **\[エラー一覧\]** でコード分析の警告を右クリックし、**\[メッセージの非表示\]** をクリックすると、コードまたはプロジェクトのグローバル抑制ファイルに **SuppressMessage** 属性が追加されます。  
  
 **SuppressMessage** 属性は次の形式で定義します。  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```c#  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 \[C\+\+\]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 指定項目:  
  
-   **Rule Category** \- 規則を定義するカテゴリ。  コード分析規則のカテゴリの詳細については、「[マネージ コードの警告に対応するコードの解析](../code-quality/code-analysis-for-managed-code-warnings.md)」を参照してください。  
  
-   **Rule Id** \- 規則の識別子。  規則識別子の短い名前と長い名前の両方を使用できます。  短い名前は CAXXXX で、長い名前は CAXXXX:FriendlyTypeName です。  
  
-   **Justification** \- メッセージを抑制する理由を説明するテキスト。  
  
-   **Message Id** \- 各メッセージが報告する問題の一意の識別子。  
  
-   **Scope** \- 警告を抑制する対象。  Target が指定されなかった場合、Scope が属性の対象に設定されます。  次のスコープがサポートされます。  
  
    -   モジュール  
  
    -   名前空間  
  
    -   リソース  
  
    -   型  
  
    -   メンバー  
  
-   **Target** \- 警告を抑制する対象を指定するための識別子。  この識別子には完全修飾項目名を使用する必要があります。  
  
## SuppressMessage の使用方法  
 コード分析の警告は、**SuppressMessage**  属性のインスタンスが適用されるレベルで抑制されます。  これは、抑制情報を違反が発生するコードに密に結合するためです。  
  
 抑制属性を指定する際、一般には、規則カテゴリと規則識別子 \(オプションで規則の名称を指定することも可能\) が使用されます。  次に例を示します。  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 パフォーマンス上の要件が厳しく、ソース内抑制のメタデータを可能な限り小さくする必要がある場合は、規則の名前を省略することができます。  規則を一意に識別するには、規則カテゴリと規則 ID だけで十分です。  次に例を示します。  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 この形式は、保守性の点でお勧めできません。  
  
## メソッド本体内の複数の違反を抑制する方法  
 属性をメソッドに対して適用することはできますが、メソッド本体に埋め込むことはできません。  ただし、識別子をメッセージ ID として指定すると、1 つのメソッドにおける同じ違反の複数の出現を識別できます。  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-cs[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## 生成されたコード  
 マネージ コード コンパイラや一部のサードパーティ製ツールは、迅速なコード開発を目的とするコードを生成します。  ソース ファイルに含まれるコンパイラ生成のコードは、通常、**GeneratedCodeAttribute** 属性でマークされます。  
  
 生成されたコードのコード分析の警告とエラーを抑制するかどうかを指定できます。  このような警告やエラーを抑制する方法については、「[方法: 生成されたコードに対する警告を抑制する](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)」を参照してください。  
  
 アセンブリ全体または 1 つのパラメーターに適用された **GeneratedCodeAttribute** 属性は、コード分析では無視されます。  このような状況はほとんど発生しません。  
  
## グローバル レベルの抑制  
 マネージ コード分析ツールは、アセンブリ、モジュール、型、メンバー、パラメーターの各レベルで適用された **SuppressMessage** 属性を調べます。  リソースおよび名前空間に対しても違反が検出されます。  これらの違反については、グローバル レベルで適用し、スコープと対象を指定する必要があります。  たとえば、次のメッセージでは、名前空間の違反が抑制されます。  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  名前空間をスコープとして警告を抑制すると、名前空間それ自体に対する警告が抑制されます。  名前空間に含まれる型に対する警告は抑制されません。  
  
 明示的にスコープを指定することにより、あらゆる違反を抑制できます。  このような抑制はグローバル レベルで指定されている必要があります。  型を修飾することによってメンバー レベルの抑制を指定することはできません。  
  
 コンパイラによって生成されたコードなど、明示的に指定されたユーザー ソースとの対応関係を持たないコードを参照するメッセージについては、必ずグローバル レベルの抑制を使用します。  たとえば、次のコードはコンパイラによって生成されたコンストラクターに対する違反を抑制します。  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  Target には、常に完全修飾項目名を指定します。  
  
## グローバル抑制ファイル  
 グローバル抑制ファイルには、グローバル レベルの違反または対象が指定されていない違反が保存されます。  たとえば、アセンブリ レベルの違反に対する抑制は、このファイルに格納されます。  また、ASP.NET に関して抑制する一部の警告もこのファイルに格納されます。フォームのコードからプロジェクト レベルの設定にアクセスすることはできないためです。  \[エラー一覧\] ウィンドウで **\[メッセージの非表示\]** コマンドの **\[プロジェクト抑制ファイル内\]** オプションを初めて選択すると、グローバル抑制が作成されてプロジェクトに追加されます。  詳細については、「[方法: メニュー項目を使用して警告を抑制する](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)」を参照してください。  
  
## 参照  
 <xref:System.Diagnostics.CodeAnalysis>