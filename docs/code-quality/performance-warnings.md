---
title: "パフォーマンスの警告 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: baf04adf4589f0809db6a2de2bedcc0efd0f6fcb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="performance-warnings"></a>パフォーマンスに関する警告
パフォーマンスの警告は、高パフォーマンスのライブラリとアプリケーションをサポートします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|ルール|説明|  
|----------|-----------------|  
|[CA1800: 不必要にキャストしません](../code-quality/ca1800-do-not-cast-unnecessarily.md)|二重のキャストがあるとパフォーマンスが低下します。特に、小さな繰り返しステートメントでキャストが実行される場合はそうです。|  
|[CA1801: 使用されていないパラメーターをレビューします](../code-quality/ca1801-review-unused-parameters.md)|メソッドのシグネチャに、メソッドの本体で使用されていないパラメーターがあります。|  
|[CA1802: 適切な場所にリテラルを使用します](../code-quality/ca1802-use-literals-where-appropriate.md)|静的および読み取り専用フィールドが宣言されて (では Shared および ReadOnly [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])、コンパイル時に計算できる値に初期化されます。 対象フィールドに割り当てられている値は、コンパイル時に計算であるため、宣言を const に変更 (で Const [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) フィールドの値が実行時ではなく、コンパイル時に計算できるようにします。|  
|[CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)|使用されていないローカル変数や不要な引数があると、アセンブリのサイズが大きくなり、パフォーマンスが低下します。|  
|[CA1806: メソッドの結果を無視しない](../code-quality/ca1806-do-not-ignore-method-results.md)|新しいオブジェクトを作成しても、使用されていませんを作成して新しい文字列を返すメソッドが呼び出されたと新しい文字列を使用しない、またはコンポーネント オブジェクト モデル (COM) または P/invoke メソッドが使用されていません。 HRESULT またはエラー コードを返します。|  
|[CA1809: ローカルを使用しすぎないでください](../code-quality/ca1809-avoid-excessive-locals.md)|パフォーマンス最適化の一般的な方法として、メモリではなくプロセッサのレジスタに値を格納する方法があります。これは "値のレジスタ格納" と呼ばれます。  すべてのローカル変数をレジスタ格納を向上させるのには、64 にローカル変数の数を制限します。|  
|[CA1810: 参照型の静的フィールドをインラインで初期化します](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|型で明示的な静的コンストラクターを宣言すると、Just-In-Time (JIT) コンパイラが、静的コンストラクターが呼び出されたことを確認するために、型の静的メソッドと静的インスタンス コンストラクターに個別にチェックを追加します。 静的コンストラクターのチェックによってパフォーマンスが低下することがあります。|  
|[CA1811: 呼び出されていないプライベート コードを使用しません](../code-quality/ca1811-avoid-uncalled-private-code.md)|プライベートまたは内部 (アセンブリ レベル) のメンバーでは、アセンブリでは、呼び出し元はありません、共通言語ランタイムによって呼び出されていませんおよびデリゲートでは呼び出されません。|  
|[CA1812: インスタンス化されていない内部クラスを使用しないでください](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|アセンブリ レベルの型のインスタンスが、アセンブリ内のコードから作成されません。|  
|[CA1813: シールされていない属性を使用しません](../code-quality/ca1813-avoid-unsealed-attributes.md)|[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] クラス ライブラリには、カスタム属性を取得するメソッドが用意されています。 既定では、これらのメソッドで属性の継承階層が検索されます。 属性をシールすると、継承階層の全体が検索されなくなるため、パフォーマンスが向上します。|  
|[CA1814: 複数次元の配列ではなくジャグ配列を使用します](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|ジャグ配列とは、その要素も配列である配列です。 要素を構成する配列は、さまざまなサイズは、小さい無駄な空間データの一部のセットで発生することができますできます。|  
|[CA1815: equals および operator equals を値型でオーバーライドします](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|値型の場合、Equals を継承した実装が Reflection ライブラリを使用して、すべてのフィールドの内容を比較します。 Reflection は計算コストが高いため、場合によってはすべてのフィールドで等値性を比較する必要はありません。 ユーザーがインスタンスの比較または並べ替えを行うことや、ハッシュ テーブル キーとしてインスタンスを使用することが予想される場合には、値型に Equals を実装する必要があります。|  
|[CA1816: GC.SuppressFinalize を正しく呼び出します](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Dispose の実装であるメソッドでは、GC は呼び出されません。SuppressFinalize、または Dispose の実装ではないメソッドは、GC を呼び出します。SuppressFinalize、またはメソッドは、GC を呼び出します。SuppressFinalize し、これ以外のものを渡します (では Me [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。|  
|[CA1819: プロパティは、配列を返すことはできません](../code-quality/ca1819-properties-should-not-return-arrays.md)|プロパティによって返される配列は書き込みで保護されている場合でも、このプロパティは読み取り専用 配列の改ざんを防ぐには、プロパティで配列のコピーを返す必要があります。 一般に、このようなプロパティを呼び出すときのパフォーマンス低下は理解されません。|  
|[CA1820: 文字列の長さを使用して空の文字列をテストします](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|String.Length プロパティまたは String.IsNullOrEmpty メソッドを使用して文字列を比較する方法は、Equals を使用する場合よりもはるかに高速です。|  
|[CA1821: 空のファイナライザーを削除します](../code-quality/ca1821-remove-empty-finalizers.md)|オブジェクトの有効期間の追跡に関連するパフォーマンス オーバーヘッドが増大するため、ファイナライザーは可能な限り使用しないでください。 空のファイナライザーが発生するメリット オーバーヘッドが増大します。|  
|[CA1822: メンバーを static に設定します](../code-quality/ca1822-mark-members-as-static.md)|インスタンス データにアクセスしない、またはインスタンス メソッドを呼び出さないメンバーは、静的 ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では共有) としてマークできます。 メソッドを静的としてマークすると、コンパイラはこれらのメンバーに対する非仮想呼び出しサイトを出力します。 パフォーマンス重視のコードでは、これにより大きくパフォーマンスを向上できます。|  
|[CA1823: 使用されていないプライベート フィールドを使用しません](../code-quality/ca1823-avoid-unused-private-fields.md)|アセンブリ内でアクセスされていないと思われるプライベート フィールドが検出されました。|  
|[CA1824: アセンブリを NeutralResourcesLanguageAttribute に設定します](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|NeutralResourcesLanguage 属性は、ResourceManager に対し、アセンブリのニュートラル カルチャのリソースを表示するために使用した言語を通知します。 これにより、読み込んだ最初のリソースに対する検索のパフォーマンスが向上し、ワーキング セットを縮小できます。|