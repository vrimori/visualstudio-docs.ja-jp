---
title: "マネージ コードの\"拡張デザイン ガイドライン規則\"規則を設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 78b9d5a2c2f147ade02e3123e2e5c08f130b29de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>マネージ コードの "拡張デザイン ガイドライン規則" 規則セット
Microsoft 拡張デザイン ガイドライン規則規則セットは、報告される、使いやすさと保守容易性の問題を最大化する基本デザイン ガイドライン規則を展開します。 特に、命名に関するガイドラインに重点が置かれています。 この規則セットを保守が容易なコードを記述する最高レベルの基準を適用するか、プロジェクトにライブラリ コードが含まれている場合を検討する必要があります。  
  
 拡張デザイン ガイドライン規則には、すべての Microsoft 基本デザイン ガイドライン規則が含まれます。 基本デザイン ガイドライン規則には、すべての Microsoft 最小推奨規則が含まれます。 詳細については、次を参照してください[マネージ コードの基本デザイン ガイドライン規則ルール設定](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)と[マネージ コードのマネージ推奨規則ルール設定。](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)  
  
 次の表では、Microsoft 拡張デザイン ガイドライン規則規則セット内のすべての規則について説明します。  
  
|ルール|説明|  
|----------|-----------------|  
|[CA 1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|破棄可能なフィールドを所有する型は、破棄可能でなければなりません|  
|[CA 1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|イベント ハンドラーを正しく宣言します。|  
|[CA 1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|アセンブリに assemblyversionattribute を設定します|  
|[CA 1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|インターフェイス メソッドは、子型によって呼び出し可能でなければなりません|  
|[CA 1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|ネイティブ リソースを所有する型は、破棄可能でなければなりません|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|P/invoke を NativeMethods クラスに移動します。|  
|[CA 1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|基本クラスのメソッドを非表示にできません。|  
|[CA 1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable を正しく実装します。|  
|[CA 1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|予期しない場所に例外を発生させません|  
|[CA 1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|アクセラレータが重複しません。|  
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/invoke エントリ ポイントが存在する必要があります。|  
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/invoke を表示することはできません。|  
|[CA 1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Auto 配置の型が COM 参照することはできません。|  
|[CA 1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|P/invoke の直後に GetLastError を呼び出します|  
|[CA 1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 参照可能な型の基本型が COM 参照可能にする必要があります。|  
|[CA 1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|COM 登録メソッドは一致しなければなりません|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/invoke を正しく宣言します。|  
|[CA 1821](../code-quality/ca1821-remove-empty-finalizers.md)|空のファイナライザーを削除します。|  
|[CA 1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|値型フィールドはポータブルでなければなりません|  
|[CA 1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P/invoke 宣言はポータブルでなければなりません|  
|[CA 2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Id が不十分なオブジェクトをロックしないでください。|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|セキュリティの脆弱性について、SQL クエリを確認します。|  
|[CA 2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/invoke 文字列引数に対してマーシャ リングを指定します。|  
|[CA 2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|値型で宣言型セキュリティを再確認します|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|ポインターを表示することはできません。|  
|[CA 2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|セキュリティで保護された型はフィールドを公開する必要があります。|  
|[CA 2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|メソッドのセキュリティは、型のスーパー セットをする必要があります。|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA メソッドは APTCA メソッドのみを呼び出す必要があります。|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 型は APTCA 基本型を拡張する必要がありますのみ|  
|[CA 2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|リンク確認要求を持つメソッドを間接的に公開しません|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|オーバーライドのリンク要求をベースと同一にする必要があります。|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|脆弱なラップ finally 句の外側 try します。|  
|[CA 2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|型のリンク要求には、継承要求が必要です。|  
|[CA 2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|セキュリティ クリティカルな型は型の等価性に参加できません。|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|既定のコンス トラクターは、少なくとも基本データ型の既定のコンス トラクターとしてほど重要である必要があります。|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|デリゲートは透過性の整合メソッドにバインドする必要があります。|  
|[CA 2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|基本メソッドをオーバーライドする場合、メソッドは透過性の整合性を保つ必要があります。|  
|[CA 2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|透過的メソッドは検証可能な IL のみを含める必要があります。|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出さないでください。|  
|[CA 2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透過的なコードは、セキュリティ上重要な項目を参照しないでください。|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透過的メソッドは、Linkdemand を満たしていない必要があります。|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|種類は、少なくともほど重要で、基本型およびインターフェイスである必要があります。|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透過的メソッドは、セキュリティを使用しない場合がありますアサート|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|ネイティブ コードに透過的なメソッドを呼び出してはなりません。|  
|[CA 2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|スタックの詳細を保持するために再スローします。|  
|[CA 2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|オブジェクトを複数回破棄しません|  
|[CA 2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|値型の静的フィールドのインラインを初期化します|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|サービス コンポーネントを WebMethod にマークしないでください。|  
|[CA 2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|破棄可能なフィールドは破棄されなければなりません|  
|[CA 2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|コンス トラクターのオーバーライド可能なメソッドを呼び出す必要はありません。|  
|[CA 2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|破棄可能な型はファイナライザーを宣言する必要があります。|  
|[CA 2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|ファイナライザーは基本クラスのファイナライザーを呼び出す必要があります。|  
|[CA 2229](../code-quality/ca2229-implement-serialization-constructors.md)|シリアル化コンス トラクターを実装します。|  
|[CA 2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|ValueType.Equals のオーバーライドで、演算子 equals をオーバー ロードします。|  
|[CA 2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Windows フォームのエントリ ポイントを stathread に設定します|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|すべてのシリアル化不可能なフィールドをマークします。|  
|[CA 2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|ISerializable 型の基底クラス メソッドを呼び出す|  
|[CA 2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|ISerializable 型を serializableattribute に設定します|  
|[CA 2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|シリアル化メソッドを正しく実装します。|  
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|ISerializable を正しく実装します。|  
|[CA 2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|書式指定メソッドに正しい引数を指定します。|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|NaN に対して正しくテストします|  
|[CA 1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|ジェネリック型で静的メンバーを宣言しません|  
|[CA 1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|ジェネリック リストを公開しません|  
|[CA 1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|ジェネリック イベント ハンドラーのインスタンスを使用します。|  
|[CA 1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|ジェネリック メソッドが型パラメーターを指定する必要があります。|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|ジェネリック型でパラメーターを回避します。|  
|[CA 1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|メンバー シグニチャ内のジェネリック型を入れ子にしないでください。|  
|[CA 1007](../code-quality/ca1007-use-generics-where-appropriate.md)|適切な場所にジェネリックを使用します|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Enums は 0 の値でなければなりません|  
|[CA 1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|コレクションは、ジェネリック インターフェイスを実装する必要があります。|  
|[CA 1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|基本型をパラメーターとして渡すことを検討してください。|  
|[CA 1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|抽象型にコンス トラクターはありません。|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|オーバー ロードで、演算子 equals をオーバー ロードが加算および減算|  
|[CA 1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|アセンブリに clscompliantattribute を設定します|  
|[CA 1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|アセンブリに comvisibleattribute を設定します|  
|[CA 1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|属性を attributeusageattribute に設定します|  
|[CA 1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|属性引数にアクセサーを定義します|  
|[CA 1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|インデクサーを多次元することはできません。|  
|[CA 1024](../code-quality/ca1024-use-properties-where-appropriate.md)|プロパティを使用して、適切な場所|  
|[CA 1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|反復する引数を params 配列で置き換えます|  
|[CA 1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|既定のパラメーターは使用できません。|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Enums を FlagsAttribute をマークします。|  
|[CA 1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|列挙ストレージは Int32 でなければなりません|  
|[CA 1030](../code-quality/ca1030-use-events-where-appropriate.md)|適切な場所にイベントを使用します。|  
|[CA 1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|一般的な例外の種類はキャッチしません|  
|[CA 1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|標準例外コンス トラクターを実装します。|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|入れ子にされた型を表示することはできません。|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|メンバーが厳密に ICollection の実装によって型指定します。|  
|[CA 1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|比較できる型でメソッドをオーバーライドします。|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|列挙子は厳密に型指定|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|リストが厳密に型指定されました。|  
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|ObsoleteAttribute メッセージを指定します。|  
|[CA 1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|整数または文字列インデクサー引数を使用します。|  
|[CA 1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|プロパティが書き込み専用することはできません。|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|参照型で、演算子 equals をオーバー ロードしません。|  
|[CA 1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Sealed 型のプロテクト メンバーを宣言しません|  
|[CA 1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Sealed 型の仮想メンバーを宣言しません|  
|[CA 1050](../code-quality/ca1050-declare-types-in-namespaces.md)|名前空間の型を宣言します。|  
|[CA 1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|インスタンス フィールドを宣言できません。|  
|[CA 1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|スタティック ホルダー型をシールする必要があります。|  
|[CA 1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|スタティック ホルダー型にコンス トラクターはありません。|  
|[CA 1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI パラメーターを文字列にする必要があることはできません。|  
|[CA 1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI 戻り値を文字列にする必要があることはできません。|  
|[CA 1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI のプロパティを文字列にする必要があることはできません。|  
|[CA 1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|文字列 URI オーバー ロードは、System.Uri オーバー ロードを呼び出す|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|種類は、特定の基本型を拡張しない必要があります。|  
|[CA 1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|メンバーが特定の具象型に公開することはできません。|  
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|例外はパブリックにする必要があります。|  
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|変数名は、フィールド名と一致する必要があります。|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|過剰な複雑さを回避します。|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|識別子は大文字/小文字以外で相違必要があります。|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|識別子はキーワードと一致しません。|  
|[CA 1801](../code-quality/ca1801-review-unused-parameters.md)|未使用のパラメーターを確認します。|  
|[CA 1804](../code-quality/ca1804-remove-unused-locals.md)|使用されていないローカルを削除します。|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|過剰なローカル変数を回避します。|  
|[CA 1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|参照型の静的フィールドのインラインを初期化します|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|呼び出されていないプライベート コードを避ける|  
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|インスタンス化されていない内部クラスを避ける|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|シールされていない属性します。|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|ジャグ配列を多次元よりも優先します。|  
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Equals をオーバーライドし、演算子 equals を値型で|  
|[CA 1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|プロパティは、配列を返す必要がありますできません。|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|文字列の長さを使用して空の文字列をテストします|  
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|マークのメンバーを static に|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|使用されていないプライベート フィールドを回避します。|  
|[CA 2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|予約済みの例外の種類を発生させません|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Win32 API に相当するマネージの使用します。|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|引数の例外を正しくインスタンス化します。|  
|[CA 2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|非定数フィールドを表示することはできません。|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Enums を FlagsAttribute のマークを付けないでください。|  
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Exception 句に例外を発生させません|  
|[CA 2221](../code-quality/ca2221-finalizers-should-be-protected.md)|ファイナライザーは保護されなければなりません|  
|[CA 2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|継承されたメンバーの可視性を縮小しません|  
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|メンバーが複数の戻り値の型が異なる必要があります。|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|オーバー ロードで、演算子 equals で equals をオーバーライド|  
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|演算子のオーバー ロード名前付けされた代替|  
|[CA 2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|演算子は対称型オーバー ロードを含まなければなりません|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|コレクションのプロパティを読み取り専用|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|可変個の引数に対して param を使用します。|  
|[CA 2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|文字列の代わりに System.Uri オブジェクトを渡します|  
|[CA 2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|オプションのフィールドに逆シリアル化メソッドを提供します。|  
|[CA1020](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|いくつかの型と名前空間を避ける|  
|[CA1021](../code-quality/ca1021-avoid-out-parameters.md)|Out パラメーターを避ける|  
|[CA1040](../code-quality/ca1040-avoid-empty-interfaces.md)|空のインターフェイスを回避します。|  
|[CA 1045](../code-quality/ca1045-do-not-pass-types-by-reference.md)|型を参照によって渡しません|  
|[CA 1062](../code-quality/ca1062-validate-arguments-of-public-methods.md)|パブリック メソッドの引数を検証します。|  
|[CA1501](../code-quality/ca1501-avoid-excessive-inheritance.md)|過剰な継承します。|  
|[CA 1504](../code-quality/ca1504-review-misleading-field-names.md)|紛らわしいフィールド名を確認します。|  
|[CA1505](../code-quality/ca1505-avoid-unmaintainable-code.md)|メンテナンスできないコードを避ける|  
|[CA1506](../code-quality/ca1506-avoid-excessive-class-coupling.md)|クラス結合度を回避します。|  
|[CA1700](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|名前を指定しません enum 値 'Reserved'|  
|[CA 1701](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|リソース文字列の複合語では、大文字と小文字が正しく区別する必要があります。|  
|[CA 1702](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|複合語では、大文字と小文字が正しく区別する必要があります。|  
|[CA 1703](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|リソース文字列を正しく入力されなければなりません|  
|[CA 1704](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|識別子は正しく入力されなければなりません|  
|[CA 1707](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|識別子はアンダー スコアを含めることはできません。|  
|[CA 1709](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|識別子では、大文字と小文字が正しく区別する必要があります。|  
|[CA1710](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|識別子は、正しいサフィックスをいなければなりません|  
|[CA1711](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|識別子は不適切なサフィックスをいなければなりません|  
|[CA 1712](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|列挙値を型名のプレフィックスにしません|  
|[CA1713](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|イベントは、before または after プレフィックスはありません。|  
|[CA1714](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|フラグ列挙は複数形の名前である必要があります。|  
|[CA1715](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|識別子は正しいプレフィックスをいなければなりません|  
|[CA1717](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|FlagsAttribute 列挙のみが複数形の名前がある必要があります。|  
|[CA1719](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|パラメーター名は、メンバー名と一致する必要があります。|  
|[CA 1720](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|識別子は型名を含めることはできません。|  
|[CA1721](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|プロパティ名が、get メソッドと一致する必要があります。|  
|[CA1722](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|識別子は不適切なプレフィックスをいなければなりません|  
|[CA1724](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|型の名前が名前空間と一致する必要があります。|  
|[CA1725](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|パラメーター名が基本宣言と一致する必要があります。|  
|[CA1726](../code-quality/ca1726-use-preferred-terms.md)|用語を使用します|  
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|リテラルを正しく入力されなければなりません|