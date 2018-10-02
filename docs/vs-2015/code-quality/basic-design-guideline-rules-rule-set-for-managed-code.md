---
title: マネージ コードの基本デザイン ガイドライン規則のルールの設定 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: aad4bb755889ca4d2aa9766836f156495d281bca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536220"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>マネージド コードの "基本デザイン ガイドライン規則" 規則セット
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[基本デザイン ガイドライン規則ルールセットのマネージ コードの](https://docs.microsoft.com/visualstudio/code-quality/basic-design-guideline-rules-rule-set-for-managed-code)します。  
  
Microsoft 基本デザイン ガイドライン規則ルールのセット、コードを簡単に理解して使用することを目的に使用できます。 この規則セットは、プロジェクトにライブラリ コードが含まれている場合、またはコードが簡単に維持するためのベスト プラクティスを適用する場合を含める必要があります。  
  
 基本のデザイン ガイドライン規則には、Microsoft 最小推奨規則のルール セット内のすべての規則が含まれます。 最小の規則の一覧は、次を参照してください。[マネージ推奨規則ルールセットのマネージ コードの](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)します。  
  
 次の表では、すべての Microsoft 基本デザイン ガイドライン規則のルール セット内の規則について説明します。  
  
|ルール|説明|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|破棄可能なフィールドを所有する型は、破棄可能でなければなりません|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|イベント ハンドラーを正しく宣言します。|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|アセンブリに assemblyversionattribute を設定します|  
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|インターフェイス メソッドは、子型によって呼び出し可能でなければなりません|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|ネイティブ リソースを所有する型は、破棄可能でなければなりません|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|P/invoke を NativeMethods クラスに移動します。|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|基底クラスのメソッドを隠ぺいしません。|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable を正しく実装します。|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|予期しない場所で例外を発生させません|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|アクセラレータが重複の回避します。|  
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/invoke エントリ ポイントが存在する必要があります。|  
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/invoke を表示することはできません。|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Auto 配置の型が COM に表示することはできません。|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|P/invoke の直後に GetLastError を呼び出します|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM から参照できる型の基本型が COM 参照可能にする必要があります。|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|COM 登録メソッドは一致する必要があります。|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/invoke を正しく宣言します。|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|空のファイナライザーを削除します。|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|値型フィールドはポータブルでなければなりません|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P/invoke 宣言はポータブルでなければなりません|  
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Id が不十分なオブジェクトをロックしないでください。|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL クエリのセキュリティの脆弱性を確認します。|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/invoke 文字列引数に対してマーシャ リングを指定します。|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|値型で宣言型セキュリティを確認してください。|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|ポインターを表示することはできません。|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|セキュリティで保護された型はフィールドを公開する必要があります。|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|メソッドのセキュリティの種類のスーパー セットである必要があります。|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA メソッドは APTCA メソッドのみを呼び出す必要があります。|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 型は APTCA 基本型のみを拡張する必要があります。|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|リンク確認要求でメソッドを間接的に公開できません。|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|オーバーライドのリンク確認要求は基本同一である必要があります。|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|ラップの脆弱性のある finally 句の外側を try します。|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|型のリンク要求には、継承要求が必要です。|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|セキュリティ クリティカルな型は型の等価性に参加できません。|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|既定のコンス トラクターは、少なくとも基本型の既定のコンス トラクターと同程度に重要である必要があります。|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|デリゲートは透過性の整合メソッドにバインドする必要があります。|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|メソッドは基本メソッドをオーバーライドするときに透過性の整合性を保つ必要があります。|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|透過的メソッドは、検証可能な IL のみを含める必要があります。|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出す必要がありますいません。|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透過的なコードは、セキュリティ上重要な項目を参照する必要があります。|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透過的メソッドは、Linkdemand を満たしていませんする必要があります。|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|種類は、少なくとも、基本型およびインターフェイスと同程度に重要である必要があります。|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透過的メソッドは、セキュリティを使用しない可能性がありますアサート|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透過的メソッドはネイティブ コードを呼び出す必要がありますいません。|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|スタックの詳細を保持するために再スローします。|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|オブジェクトを複数回破棄しません|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|値型の静的フィールドのインラインを初期化します|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|サービス コンポーネントを webmethod に設定をマークしないでください。|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|破棄可能なフィールドを破棄する必要があります。|  
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|コンス トラクターのオーバーライド可能なメソッドを呼び出しません|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|破棄可能な型はファイナライザーを宣言する必要があります。|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|ファイナライザーは基本クラスのファイナライザーを呼び出す必要があります。|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|シリアル化コンス トラクターを実装します。|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|ValueType.Equals のオーバーライドで、演算子 equals をオーバー ロードします。|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Mark の Windows フォームのエントリ ポイントを stathread に設定します|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|すべてのシリアル化不可能なフィールドをマークします。|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|ISerializable 型の基本クラス メソッドを呼び出す|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|ISerializable 型を serializableattribute に設定します|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|シリアル化メソッドを正しく実装します。|  
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|ISerializable を正しく実装します。|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|書式指定メソッドに正しい引数を指定します。|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|NaN に対して正しくテストします|  
|[CA 1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|ジェネリック型で静的メンバーを宣言しません|  
|[CA 1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|ジェネリック リストを公開しません|  
|[CA 1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|汎用イベント ハンドラーのインスタンスを使用して、|  
|[CA 1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|ジェネリック メソッドは、型パラメーターを指定する必要があります。|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|ジェネリック型で過剰なパラメーターを回避します。|  
|[CA 1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|ジェネリック型メンバー シグネチャ内で入れ子にしません|  
|[CA 1007](../code-quality/ca1007-use-generics-where-appropriate.md)|適切な場所にジェネリックを使用します。|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|列挙がゼロの値|  
|[CA 1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|コレクションは、ジェネリック インターフェイスを実装する必要があります。|  
|[CA 1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|基本型をパラメーターとして渡すことを検討してください。|  
|[CA 1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|抽象型には、コンス トラクターはありません。|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|オーバー ロードで、演算子 equals をオーバー ロードの加算および減算|  
|[CA 1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|アセンブリに clscompliantattribute を設定します|  
|[CA 1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|アセンブリに comvisibleattribute を設定します|  
|[CA 1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|属性を attributeusageattribute に設定します|  
|[CA 1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|属性引数にアクセサーを定義します|  
|[CA 1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|インデクサーを多次元することはできません。|  
|[CA 1024](../code-quality/ca1024-use-properties-where-appropriate.md)|適切な場所のプロパティを使用します。|  
|[CA 1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|反復する引数を params 配列で置き換えます|  
|[CA 1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|既定のパラメーターは使用できません。|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|FlagsAttribute で列挙をマークします。|  
|[CA 1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|列挙ストレージは Int32 でなければなりません|  
|[CA 1030](../code-quality/ca1030-use-events-where-appropriate.md)|適切な場所、イベントを使用します。|  
|[CA 1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|一般的な例外の種類はキャッチしません|  
|[CA 1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|標準例外コンス トラクターを実装します。|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|入れ子にされた型を表示することはできません。|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|ICollection の実装には、メンバーが厳密に型指定します。|  
|[CA 1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|比較可能な型のメソッドをオーバーライドします。|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|列挙子を厳密に型指定する必要があります。|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|リストは厳密に型指定します。|  
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|ObsoleteAttribute メッセージを指定します。|  
|[CA 1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|インデクサーは整数または文字列引数を使用して、|  
|[CA 1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|プロパティが書き込み専用することはできません。|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|参照型で、演算子 equals をオーバー ロードしません。|  
|[CA 1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Sealed 型の保護されたメンバーを宣言しません|  
|[CA 1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Sealed 型の仮想メンバーを宣言しません|  
|[CA 1050](../code-quality/ca1050-declare-types-in-namespaces.md)|名前空間の型を宣言します。|  
|[CA 1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|インスタンス フィールドを宣言しません|  
|[CA 1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|スタティック ホルダー型をシールする必要があります。|  
|[CA 1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|スタティック ホルダー型には、コンス トラクターはありません。|  
|[CA 1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI パラメーターは文字列をすることはできません。|  
|[CA 1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI 戻り値は文字列をすることはできません。|  
|[CA 1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI のプロパティには、文字列がすることはできません。|  
|[CA 1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|文字列 URI オーバー ロードは、System.Uri オーバー ロードを呼び出す|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|種類は一定の基本型を拡張する必要がありません。|  
|[CA 1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|メンバーが特定の具象型に公開することはできません。|  
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|例外はパブリックである必要があります。|  
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|変数名は、フィールド名と一致する必要があります。|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|過剰な複雑さを回避します。|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|識別子は、ケース以外で相違させる必要があります。|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|識別子は、キーワードと一致する必要があります。|  
|[CA 1801](../code-quality/ca1801-review-unused-parameters.md)|未使用のパラメーターをレビューします|  
|[CA 1804](../code-quality/ca1804-remove-unused-locals.md)|使用されていないローカルを削除します|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|過剰なローカルします。|  
|[CA 1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|参照型の静的フィールドのインラインを初期化します|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|呼び出されていないプライベート コードを避ける|  
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|インスタンス化されていない内部クラスを回避します。|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|シールされていない属性します。|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|多次元よりジャグ配列を優先します。|  
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Equals をオーバーライドし、演算子 equals を値型|  
|[CA 1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|プロパティは、配列を返す必要がありますいません。|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|文字列の長さを使用して空の文字列をテスト|  
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|静的メンバーをマーク|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|使用されていないプライベート フィールドを回避します。|  
|[CA 2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|予約された例外の種類を発生させません|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Win32 API に相当するマネージドの使用します。|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|引数の例外を正しくインスタンス化します。|  
|[CA 2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|非定数フィールドを表示することはできません。|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|FlagsAttribute で列挙をマークしないでください。|  
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Exception 句に例外を発生させません|  
|[CA 2221](../code-quality/ca2221-finalizers-should-be-protected.md)|ファイナライザーは保護する必要があります。|  
|[CA 2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|継承されたメンバーの可視性を縮小しません|  
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|メンバーが複数の戻り値の型が異なる必要があります。|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|オーバー ロードする演算子 equals で equals をオーバーライド|  
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|演算子のオーバー ロード名前付けされた代替|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|演算子は対称型オーバー ロードである必要があります。|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|コレクションのプロパティは読み取り専用にします。|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|可変個の引数に対して param を使用します。|  
|[CA 2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|文字列の代わりに System.Uri オブジェクトを渡します|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|オプションのフィールドに逆シリアル化メソッドを提供します。|



