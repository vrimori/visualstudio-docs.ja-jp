---
title: マネージ コードの"マネージ推奨規則"規則の設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 33c35304643d0743b5da53a75cae9a01125b7da6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296102"
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>マネージド コードの "マネージ推奨規則" 規則セット
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

潜在的なセキュリティ ホール、アプリケーションのクラッシュ、その他の重要なロジックとデザイン エラーなど、マネージ コードで最も重要な問題に集中する設定の Microsoft マネージ推奨規則規則を使用することができます。 この規則セットは、プロジェクト用に作成したカスタム規則セットを含める必要があります。  
  
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



