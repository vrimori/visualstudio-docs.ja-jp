---
title: マネージ コードの"拡張正確性規則"規則の設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cebb3f492bb3aec873f503c2efcacb7220ec9739
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187429"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>マネージド コードの "拡張正確性規則" 規則セット
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft 拡張正確性規則のルール セットは、コード分析によって報告されるロジックとフレームワーク使用エラーを最大化します。 COM 相互運用性やモバイル アプリケーションなどの特定のシナリオには、重点が置かれています。 この規則セットは、プロジェクトまたはプロジェクトに追加の問題を見つけるためにこれらのシナリオのいずれかが適用される場合などを考慮する必要があります。  
  
 Microsoft 拡張正確性規則のルール セットには、Microsoft 基本正確性規則のルールで設定された規則が含まれています。 基本的な正確性規則には、Microsoft 最小推奨規則のルールで設定される規則が含まれます。 詳細については、次を参照してください[基本正確性規則ルールセットのマネージ コードの](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)と[マネージ推奨規則のルールは、マネージ コードの設定。](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)  
  
 次の表では、すべての Microsoft 拡張正確性規則のルール セット内の規則について説明します。  
  
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
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|列挙がゼロの値|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|オーバー ロードで、演算子 equals をオーバー ロードの加算および減算|  
|[CA 1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|ローカライズされたパラメーターとしてリテラルを渡さないでください。|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|文字列を大文字に正規化します。|  
|[CA 1806](../code-quality/ca1806-do-not-ignore-method-results.md)|メソッドの結果を無視しません。|  
|[CA 1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|GC を呼び出します。SuppressFinalize 正しく|  
|[CA 1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|プロパティは、配列を返す必要がありますいません。|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|文字列の長さを使用して空の文字列をテスト|  
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|対象のフレームワークから API のみを使用します。|  
|[CA 2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|GC への呼び出しを削除します。KeepAlive|  
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|SafeHandle を使用して、ネイティブ リソースをカプセル化するには|  
|[CA 2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|汎用ハンドラーで非 CLSCompliant の例外をキャッチします。|  
|[CA 2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|読み取りのみ変更可能な参照型を宣言しません|  
|[CA 2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|配列フィールドいない読み取り専用にします。|  
|[CA 2106](../code-quality/ca2106-secure-asserts.md)|セキュリティで保護されたアサートします。|  
|[CA 2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|GC を呼び出します。KeepAlive ネイティブ リソースを使用する場合|  
|[CA 2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|プライベート インターフェイスを満たすメソッドをシールします|  
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|セキュリティで保護されたシリアル化コンス トラクター|  
|[CA 2121](../code-quality/ca2121-static-constructors-should-be-private.md)|静的コンス トラクターはプライベートでなければなりません|  
|[CA 2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|セキュリティ上重要な定数は透過的にする必要があります。|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Win32 API に相当するマネージドの使用します。|  
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Dispose メソッドが基底クラス dispose を呼び出す必要があります。|  
|[CA 2221](../code-quality/ca2221-finalizers-should-be-protected.md)|ファイナライザーは保護する必要があります。|  
|[CA 2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|継承されたメンバーの可視性を縮小しません|  
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|メンバーが複数の戻り値の型が異なる必要があります。|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|オーバー ロードする演算子 equals で equals をオーバーライド|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|演算子は対称型オーバー ロードである必要があります。|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|コレクションのプロパティは読み取り専用にします。|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|オプションのフィールドに逆シリアル化メソッドを提供します。|  
|[CA 1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|標準例外コンス トラクターを実装します。|  
|[CA 1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI パラメーターは文字列をすることはできません。|  
|[CA 1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI 戻り値は文字列をすることはできません。|  
|[CA 1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI のプロパティには、文字列がすることはできません。|  
|[CA 1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|文字列 URI オーバー ロードは、System.Uri オーバー ロードを呼び出す|  
|[CA 1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|COM 参照可能インターフェイスでのオーバー ロードを避ける|  
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Visual Basic 6 クライアントに対しては Int64 引数を避ける|  
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|COM 参照可能な型で静的メンバーを回避します。|  
|[CA 1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|AutoDual ClassInterfaceType を使用します。|  
|[CA 1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Com 参照可能な型は、可能でなければなりません|  
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|COM 登録メソッドを表示することはできません。|  
|[CA 1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|ComSource インターフェイスを IDispatch として設定します|  
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|COM 参照可能な値の型で非パブリック フィールドを回避します。|  
|[CA 1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|ブール型の P/invoke 引数を marshalas に設定します|  
|[CA 1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|アイドル状態のプロセスの優先順位を使用しないでください。|  
|[CA 1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|電源状態の変更を妨げるタイマーを使用しないでください。|  
|[CA1824](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|アセンブリを neutralresourceslanguageattribute に設定します|  
|[CA 2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|問題のあるメソッドは呼び出しません|  
|[CA 2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|ファイバーをスレッドとして処理しません|  
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|レベル 2 のアセンブリは Linkdemand を含めることはできません。|  
|[CA 2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|メンバーには、透過性注釈の競合はありません。|  
|[CA 2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|透過的メソッドは、HandleProcessCorruptingExceptions 属性を使用可能性があります。|  
|[CA 2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|LinkDemands を透過的なコードを保護する必要がありません。|  
|[CA 2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|透過的メソッドは、セキュリティ要求を使用しないでください。|  
|[CA 2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|透過的なコードは、バイト配列からアセンブリを読み込めません|  
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|透過的なメソッドが、SuppressUnmanagedCodeSecurityAttribute で修飾されていない必要があります。|  
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|リテラルは正しく入力されなければなりません|  
|[CA 2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|非定数フィールドを表示することはできません。|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|FlagsAttribute で列挙をマークしないでください。|  
|[CA2218](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|Equals をオーバーライドの GetHashCode をオーバーライドします。|  
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Exception 句に例外を発生させません|  
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|演算子のオーバー ロード名前付けされた代替|  
|[CA 2228](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|未公開のリソース形式を出荷しません|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|可変個の引数に対して param を使用します。|  
|[CA 2233](../code-quality/ca2233-operations-should-not-overflow.md)|操作はオーバーフローできません。|  
|[CA 2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|文字列の代わりに System.Uri オブジェクトを渡します|  
|[CA 2243](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|属性文字列リテラルは、正しく解析する必要があります。|



