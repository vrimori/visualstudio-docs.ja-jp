---
title: "パフォーマンスの警告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.performancerules"
helpviewer_keywords: 
  - "警告、パフォーマンス"
  - "パフォーマンスに関する警告"
  - "パフォーマンス、警告"
  - "マネージ コード分析の警告、パフォーマンスに関する警告"
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# パフォーマンスの警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

パフォーマンスの警告は、高パフォーマンスのライブラリとアプリケーションをサポートします。  
  
## このセクションの内容  
  
|規則|説明|  
|--------|--------|  
|[CA1800: 不必要にキャストしません](../code-quality/ca1800-do-not-cast-unnecessarily.md)|二重のキャストがあるとパフォーマンスが低下します。特に、小さな繰り返しステートメントでキャストが実行される場合はそうです。|  
|[CA1801: 使用されていないパラメーターを再確認します](../Topic/CA1801:%20Review%20unused%20parameters.md)|メソッドのシグネチャに、メソッドの本体で使用されていないパラメーターがあります。|  
|[CA1802: 適切な場所にリテラルを使用します](../code-quality/ca1802-use-literals-where-appropriate.md)|フィールドが static および read\-only \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では Shared および ReadOnly\) として宣言され、コンパイル時に計算できる値によって初期化されています。  対象フィールドに代入された値はコンパイル時に計算できるので、宣言を const \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では Const\) フィールドに変更して、値が実行時ではなくコンパイル時に計算されるようにします。|  
|[CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)|使用されていないローカル変数や不要な引数があると、アセンブリのサイズが大きくなり、パフォーマンスが低下します。|  
|[CA1806: メソッドの結果を無視しない](../code-quality/ca1806-do-not-ignore-method-results.md)|新しく作成されたオブジェクトが現在まで使用されていないか、新しい文字列を作成して返すメソッドが呼び出されて作成された新しい文字列が現在まで使用されていません。あるいは、コンポーネント オブジェクト モデル \(COM: Component Object Model\) または P\/Invoke メソッドから返された HRESULT またはエラー コードが現在まで使用されていません。|  
|[CA1809: ローカルを使用しすぎないでください](../code-quality/ca1809-avoid-excessive-locals.md)|パフォーマンス最適化の一般的な方法として、メモリではなくプロセッサのレジスタに値を格納する方法があります。これは "値のレジスタ格納" と呼ばれます。すべてのローカル変数をレジスタ格納できるようにするには、ローカル変数の数を 64 個に制限します。|  
|[CA1810: 参照型の静的フィールドをインラインで初期化します](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|型で明示的な静的コンストラクターを宣言すると、Just\-In\-Time \(JIT\) コンパイラが、静的コンストラクターが呼び出されたことを確認するために、型の静的メソッドと静的インスタンス コンストラクターに個別にチェックを追加します。  静的コンストラクターのチェックによってパフォーマンスが低下することがあります。|  
|[CA1811: 呼び出されていないプライベート コードを使用しません](../code-quality/ca1811-avoid-uncalled-private-code.md)|プライベート メンバーまたは内部 \(アセンブリ レベル\) メンバーが、アセンブリ内において、また共通言語ランタイムおよびデリゲートのいずれからも呼び出されていません。|  
|[CA1812: インスタンス化されていない内部クラスを使用しないでください](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)|アセンブリ レベルの型のインスタンスが、アセンブリ内のコードから作成されません。|  
|[CA1813: シールされていない属性を使用しません](../code-quality/ca1813-avoid-unsealed-attributes.md)|[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] クラス ライブラリには、カスタム属性を取得するメソッドが用意されています。  既定では、これらのメソッドで属性の継承階層が検索されます。  属性をシールすると、継承階層の全体が検索されなくなるため、パフォーマンスが向上します。|  
|[CA1814: 複数次元の配列ではなくジャグ配列を使用します](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|ジャグ配列とは、その要素も配列である配列です。  要素を構成する配列のサイズは異なってもよいため、データ セットによっては無駄な空間が少なくなります。|  
|[CA1815: equals および operator equals を値型でオーバーライドします](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)|値型の場合、Equals を継承した実装が Reflection ライブラリを使用して、すべてのフィールドの内容を比較します。  Reflection は計算コストが高いため、場合によってはすべてのフィールドで等値性を比較する必要はありません。  ユーザーがインスタンスの比較または並べ替えを行うことや、ハッシュ テーブル キーとしてインスタンスを使用することが予想される場合には、値型に Equals を実装する必要があります。|  
|[CA1816: GC.SuppressFinalize を正しく呼び出します](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Dispose を実装するメソッドが GC.SuppressFinalize を呼び出していないか、Dispose を実装しないメソッドが GC.SuppressFinalize を呼び出しています。または、あるメソッドが GC.SuppressFinalize を呼び出し、this \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では Me\) 以外のオブジェクトを渡しています。|  
|[CA1819: プロパティは、配列を返すことはできません](../code-quality/ca1819-properties-should-not-return-arrays.md)|プロパティが読み取り専用であっても、プロパティで返される配列は書き込みから保護されません。  配列の改ざんを防ぐには、プロパティで配列のコピーを返す必要があります。  一般に、このようなプロパティを呼び出すときのパフォーマンス低下は理解されません。|  
|[CA1820: 文字列の長さを使用して空の文字列をテストします](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|String.Length プロパティまたは String.IsNullOrEmpty メソッドを使用して文字列を比較する方法は、Equals を使用する場合よりもはるかに高速です。|  
|[CA1821: 空のファイナライザーを削除します](../code-quality/ca1821-remove-empty-finalizers.md)|オブジェクトの有効期間の追跡に関連するパフォーマンス オーバーヘッドが増大するため、ファイナライザーは可能な限り使用しないでください。  空のファイナライザーを使用すると、オーバーヘッドが増大するだけで何の利点もありません。|  
|[CA1822: メンバーを static に設定します](../Topic/CA1822:%20Mark%20members%20as%20static.md)|インスタンス データにアクセスしない、またはインスタンス メソッドを呼び出さないメンバーは、静的 \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では共有\) としてマークできます。  メソッドを静的としてマークすると、コンパイラはこれらのメンバーに対する非仮想呼び出しサイトを出力します。  パフォーマンス重視のコードでは、これにより大きくパフォーマンスを向上できます。|  
|[CA1823: 使用されていないプライベート フィールドを使用しません](../code-quality/ca1823-avoid-unused-private-fields.md)|アセンブリ内でアクセスされていないと思われるプライベート フィールドが検出されました。|  
|[CA1824: アセンブリを NeutralResourcesLanguageAttribute に設定します](../Topic/CA1824:%20Mark%20assemblies%20with%20NeutralResourcesLanguageAttribute.md)|NeutralResourcesLanguage 属性は、ResourceManager に対し、アセンブリのニュートラル カルチャのリソースを表示するために使用した言語を通知します。  これにより、読み込んだ最初のリソースに対する検索のパフォーマンスが向上し、ワーキング セットを縮小できます。|