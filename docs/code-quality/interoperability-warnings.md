---
title: 相互運用性に関する警告
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ef72695afba37a8a044418ad1dbd49ea6867226
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000342"
---
# <a name="interoperability-warnings"></a>相互運用性に関する警告

相互運用性の警告は、COM クライアントとのやり取りをサポートします。

## <a name="in-this-section"></a>このセクションの内容

| ルール | 説明 |
| - | - |
| [CA1400:P/invoke エントリ ポイントが存在する必要があります。](../code-quality/ca1400-p-invoke-entry-points-should-exist.md) | パブリック メソッドまたはプロテクト メソッドが System.Runtime.InteropServices.DllImportAttribute 属性を使用してマークされています。 アンマネージ ライブラリの位置を特定できないか、メソッドがライブラリ内の関数と一致しません。 |
| [CA1401:P/invoke を表示することはできません。](../code-quality/ca1401-p-invokes-should-not-be-visible.md) | パブリック型の public または protected のメソッドには、(Visual Basic で Declare キーワードを使用して実装も) System.Runtime.InteropServices.DllImportAttribute 属性があります。 このようなメソッドは公開しないでください。 |
| [CA 1402:COM 参照可能インターフェイスでのオーバー ロードを避ける](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md) | オーバーロードされたメソッドが COM クライアントに公開されると、最初のメソッド オーバーロードだけが名前を保持します。 後続のオーバーロードは、名前にアンダースコア文字 (_) およびオーバーロードの宣言の順序に対応する整数が付加され、一意の名前に変更されます。 |
| [CA 1403:Auto 配置の型が COM に表示することはできません。](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md) | COM 参照可能な値型が、LayoutKind.Auto に設定された System.Runtime.InteropServices.StructLayoutAttribute 属性を使用してマークされています。これらの型のレイアウトは、COM クライアントが特定のレイアウトが予期される動作しなくなる .NET Framework のバージョン間で変更できます。 |
| [CA 1404:P/invoke の直後に GetLastError を呼び出します](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md) | Marshal.GetLastWin32Error メソッドまたは同等に呼び出し[!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)]GetLastError 関数が、直前の呼び出しでないプラットフォームにメソッドを呼び出します。 |
| [CA 1405:COM から参照できる型の基本型が COM 参照可能にする必要があります。](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md) | COM 参照可能な型が、COM 参照不可能な型から派生しています。 |
| [CA1406:Visual Basic 6 クライアントに対しては Int64 引数を避ける](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md) | Visual Basic 6 COM クライアントは、64 ビット整数値にアクセスできません。 |
| [CA1407:COM 参照可能な型で静的メンバーを回避します。](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md) | COM では静的メソッドをサポートしていません。 |
| [CA 1408:AutoDual ClassInterfaceType を使用します。](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md) | デュアル インターフェイスを使用する型を使用することで、クライアントを特定のインターフェイス レイアウトに対応付けることができます。 将来のバージョンで、この型またはその基本型のレイアウトに変更が加えられると、インターフェイスに対応付けられた COM クライアントが切り離されます。 既定では、ClassInterfaceAttribute 属性が指定されていない場合、ディスパッチ専用インターフェイスが使用されます。 |
| [CA 1409:Com 参照可能な型は、可能でなければなりません](../code-quality/ca1409-com-visible-types-should-be-creatable.md) | COM から参照できると明確にマークされている参照型に、パブリックのパラメーター付きコンストラクターが含まれますが、パブリックの既定 (パラメーターなし) コンストラクターが含まれません。 パブリックの既定コンストラクターがない型は、COM クライアントで作成できません。 |
| [CA 1410:COM 登録メソッドは一致する必要があります。](../code-quality/ca1410-com-registration-methods-should-be-matched.md) | 使用してマークされているメソッドを宣言する型、<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>属性を使用してマークされているメソッドを宣言しません、<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>属性、またはその逆です。 |
| [CA1411:COM 登録メソッドを表示することはできません。](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md) | System.Runtime.InteropServices.ComRegisterFunctionAttribute 属性または System.Runtime.InteropServices.ComUnregisterFunctionAttribute 属性を使用してマークされているメソッドは、外部で表示されます。 |
| [CA 1412:ComSource インターフェイスを IDispatch として設定します](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md) | 型が System.Runtime.InteropServices.ComSourceInterfacesAttribute 属性によってマークされていますが、1 つ以上の指定されたインターフェイスが ComInterfaceType.InterfaceIsIDispatch に設定された System.Runtime.InteropServices.InterfaceTypeAttribute 属性によってマークされていません。 |
| [CA1413:COM 参照可能な値の型で非パブリック フィールドを回避します。](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | COM から参照できる値型の非パブリック インスタンス フィールドは、COM クライアントで表示できます。 フィールドの内容をレビューして、公開するべきではない情報や、設計またはセキュリティに意図しない影響を及ぼす情報が含まれていないかどうかを確認してください。 |
| [CA 1414:ブール型の P/invoke 引数を marshalas に設定します](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | Boolean データ型は、アンマネージ コードの複数の表現を持っています。 |
| [CA1415:P/invoke を正しく宣言します。](../code-quality/ca1415-declare-p-invokes-correctly.md) | このルールがプラットフォーム呼び出しメソッド宣言を対象に検索[!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)]を OVERLAPPED へのポインターを持つ関数がパラメーターを構造体し、対応するマネージ型のパラメーターへのポインターでない、<xref:System.Threading.NativeOverlapped?displayProperty=fullName>構造体。 |