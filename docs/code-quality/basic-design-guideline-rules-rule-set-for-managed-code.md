---
title: "マネージ コードの &quot;基本デザイン ガイドライン規則&quot; 規則セット | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# マネージ コードの &quot;基本デザイン ガイドライン規則&quot; 規則セット
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

"Microsoft 基本デザイン ガイドライン規則" 規則セットを使用すると、コードの理解と使用をより簡単にすることに専念できます。  この規則セットは、プロジェクトにライブラリ コードが含まれる場合や、保守が容易なコードを実現するためにべスト プラクティスを適用する場合に使用してください。  
  
 "基本デザイン ガイドライン規則" には、"Microsoft 最小推奨規則" 規則セット内のすべての規則が含まれます。  最小規則の一覧については、「[マネージ コードの "マネージ推奨規則" 規則セット](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)」を参照してください。  
  
 "Microsoft 基本デザイン ガイドライン規則" 規則セット内のすべての規則について、以下の表で説明します。  
  
|規則|説明|  
|--------|--------|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|破棄可能なフィールドを所有する型は、破棄可能でなければなりません|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|イベント ハンドラーを正しく宣言します|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|アセンブリに AssemblyVersionAttribute を設定します|  
|[CA1033](../Topic/CA1033:%20Interface%20methods%20should%20be%20callable%20by%20child%20types.md)|インターフェイス メソッドは、子型によって呼び出し可能でなければなりません|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|ネイティブ リソースを所有する型は、破棄可能でなければなりません|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|P\/Invoke を NativeMethods クラスに移動します|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|基底クラス メソッドを非表示にしません|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable を正しく実装します|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|予期しない場所に例外を発生させません|  
|[CA1301](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|重複するアクセラレータを使用しません|  
|[CA1400](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)|P\/Invoke エントリ ポイントは存在しなければなりません|  
|[CA1401](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)|P\/Invoke は参照可能であることはできません|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Auto 配置の型を COM 参照可能にすることはできません|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|P\/Invoke の直後に GetLastError を呼び出します|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 参照可能な型の基本型は COM 参照可能でなければなりません|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|COM 登録メソッドは一致しなければなりません|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P\/Invoke を正しく宣言します|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|空のファイナライザーを削除します|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|値型フィールドはポータブルでなければなりません|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P\/Invoke 宣言はポータブルでなければなりません|  
|[CA2002](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|弱い ID を伴うオブジェクト上でロックしません|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL クエリのセキュリティ脆弱性を確認|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P\/Invoke 文字列引数に対してマーシャリングを指定します|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|値型での宣言セキュリティを確認します|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|ポインターは参照可能にすることはできません|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|セキュリティで保護された型はフィールドを公開してはなりません|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|メソッド セキュリティは型のスーパーセットでなければなりません|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|APTCA メソッドは APTCA メソッドのみを呼び出すことができます|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 型は APTCA 基本型のみを拡張することができます|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|リンク要求を含むメソッドを間接的に公開しません|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|オーバーライドのリンク確認要求はベースと同様です。|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|脆弱性のある finally 句を外側の try でラップします|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|型のリンク要求には継承要求が必要です|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|セキュリティが重要な型は型の等価性に参加しないことがあります。|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|既定のコンストラクターは、基本型の既定コンストラクターと同程度以上、重要であることが必要|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|デリゲートは、一貫した透過性でメソッドにバインドしなければなりません|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|メソッドと基本メソッドをオーバーライドする場合、一貫した透過性を保持する必要があります|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|透過的メソッドは、検証可能な IL だけです|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透過的メソッドが、SuppressUnmanagedCodeSecurity 属性のメソッドを呼び出すことはできません|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透過的なコードではセキュリティが重要な重要項目を参照することはできません。|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透過的メソッドは LinkDemands を満たすことはできません|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|型は、基本型およびインターフェイスと同程度以上、重要でなければならない|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透過的メソッドにはセキュリティ アサートを使用できない場合もあります。|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透過的メソッドは、ネイティブ コードを呼び出す必要があります|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|スタック詳細を保持するために再度スローします。|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|オブジェクトを複数回破棄しない|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|値型のスタティック フィールドのインラインを初期化します|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|サービス コンポーネントを WebMethod に設定しません|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|破棄可能なフィールドは破棄されなければなりません|  
|[CA2214](../Topic/CA2214:%20Do%20not%20call%20overridable%20methods%20in%20constructors.md)|コンストラクターのオーバーライド可能なメソッドを呼び出しません|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|破棄可能な型はファイナライザーを宣言しなければなりません|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|ファイナライザーは基底クラスのファイナライザーを呼び出さなければなりません|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|シリアル化コンストラクターを実装します|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします。|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Windows フォームのエントリ ポイントを STAThread に設定します|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|すべてのシリアル化不可能なフィールドを設定します|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|ISerializable 型で基底クラス メソッドを呼び出します|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|ISerializable 型を SerializableAttribute に設定します|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|シリアル化メソッドを正しく実装します|  
|[CA2240](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)|ISerializable を正しく実装します|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|書式設定メソッドに正しい引数を提供|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|NaN に対して正しくテストします|  
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|ジェネリック型の静的メンバーを宣言しません|  
|[CA1002](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)|ジェネリック リストを公開しません|  
|[CA1003](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)|汎用イベント ハンドラーのインスタンスを使用します|  
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|ジェネリック メソッドは型パラメーターを指定しなければなりません|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|ジェネリック型でパラメーターを使用しすぎないでください|  
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|ジェネリック型をメンバー シグネチャ内で入れ子にしません|  
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|適切な場所にジェネリックを使用します|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Enums は 0 値を含んでいなければなりません|  
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|コレクションは、ジェネリック インターフェイスを実装しなければなりません|  
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|基本型をパラメーターとして渡すことを考慮します|  
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|抽象型はコンストラクターを含むことはできません|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|オーバーロードする加算および減算で、演算子 equals をオーバーロードします。|  
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|アセンブリに CLSCompliantAttribute を設定します|  
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|アセンブリに ComVisibleAttribute を設定します|  
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|属性を AttributeUsageAttribute に設定します|  
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|属性引数にアクセサーを定義します|  
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|インデクサーを多次元にすることはできません|  
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|適切な場所にプロパティを使用します|  
|[CA1025](../Topic/CA1025:%20Replace%20repetitive%20arguments%20with%20params%20array.md)|反復する引数を params 配列で置き換えます|  
|[CA1026](../Topic/CA1026:%20Default%20parameters%20should%20not%20be%20used.md)|既定パラメーターを使用することはできません|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|enums を FlagsAttribute に設定します|  
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|列挙ストレージは Int32 でなければなりません|  
|[CA1030](../Topic/CA1030:%20Use%20events%20where%20appropriate.md)|適切な場所にイベントを使用します|  
|[CA1031](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)|一般的な例外の種類はキャッチしません|  
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|標準例外コンストラクターを実装します|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|入れ子にされた型を参照可能にすることはできません|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|ICollection の実装は、厳密に型指定されたメンバーを含んでいます|  
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|比較可能な型でメソッドをオーバーライドします|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|列挙子は厳密に型指定されていなければなりません|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|リストは厳密に型指定されています|  
|[CA1041](../Topic/CA1041:%20Provide%20ObsoleteAttribute%20message.md)|ObsoleteAttribute メッセージを指定します|  
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|インデクサーには整数または文字列引数を使用します|  
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|プロパティを書き込み専用にすることはできません|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|参照型で、演算子 equals をオーバーロードしないでください|  
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Sealed 型の保護されたメンバーを宣言しません|  
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Sealed 型の仮想メンバーを宣言しません|  
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|名前空間で型を宣言します|  
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|参照可能なインスタンス フィールドを宣言しません|  
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|スタティック ホルダー型はシールされていなければなりません|  
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|スタティック ホルダー型はコンストラクターを含むことはできません|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI パラメーターを文字列にすることはできません|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI 戻り値を文字列にすることはできません|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI プロパティを文字列にすることはできません|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|文字列 URI オーバーロードが、System.Uri オーバーロードを呼び出します|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|型は、一定の基本型を拡張することはできません|  
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|メンバーは特定の具象型を公開しないでください。|  
|[CA1064](../Topic/CA1064:%20Exceptions%20should%20be%20public.md)|例外は public として設定する必要があります|  
|[CA1500](../Topic/CA1500:%20Variable%20names%20should%20not%20match%20field%20names.md)|変数名はフィールド名と同一にすることはできません|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|メソッドの実装を複雑にしすぎないでください|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|識別子は、大文字と小文字の区別以外にも相違していなければなりません|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|識別子はキーワードと同一にすることはできません|  
|[CA1801](../Topic/CA1801:%20Review%20unused%20parameters.md)|使用されていないパラメーターの確認|  
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|使用されていないローカルを削除します|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|ローカルを使用しすぎないでください|  
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|参照型の静的フィールドをインラインで初期化します|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|呼び出されていないプライベート コードを使用しません|  
|[CA1812](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)|インスタンス化されていない内部クラスを使用しません|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|シールされていない属性を使用しません|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|複数次元の配列ではなくジャグ配列を使用します|  
|[CA1815](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)|equals および operator equals を値型でオーバーライドします|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|プロパティは、配列を返すことはできません。|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|文字列の長さを使用して空の文字列をテストします|  
|[CA1822](../Topic/CA1822:%20Mark%20members%20as%20static.md)|メンバーを static に設定します|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|使用されていないプライベート フィールドを使用しません|  
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|予約された例外の種類を発生させません|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Win32 API に相当するマネージ API を使用します|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|引数の例外を正しくインスタンス化します|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|非定数フィールドは表示されません|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|enums を FlagsAttribute に設定しません|  
|[CA2219](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)|exception 句に例外を発生させないでください|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|ファイナライザーは保護されなければなりません|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|継承されたメンバーの参照範囲を縮小しません|  
|[CA2223](../Topic/CA2223:%20Members%20should%20differ%20by%20more%20than%20return%20type.md)|メンバーは、戻り値の型以外にも異なる点がなければなりません|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|演算子の Equals のオーバーロードのオーバーライドである|  
|[CA2225](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)|演算子オーバーロードには名前付けされた代替が存在します|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|演算子は対称型オーバーロードを含まなければなりません|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Collection プロパティは読み取り専用でなければなりません|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|可変引数に対して param を使用します|  
|[CA2234](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)|文字列の代わりに System.Uri オブジェクトを渡します|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|省略可能なフィールドに、逆シリアル化メソッドを指定します|