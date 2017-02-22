---
title: "相互運用性の警告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.Interoperabilityrules"
helpviewer_keywords: 
  - "マネージ コード分析の警告、相互運用性に関する警告"
  - "相互運用性に関する警告"
  - "警告、相互運用性"
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 相互運用性の警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

相互運用性の警告は、COM クライアントとの相互作用をサポートします。  
  
## このセクションの内容  
  
|規則|説明|  
|--------|--------|  
|[CA1400: P\/Invoke エントリ ポイントは存在しなければなりません](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)|パブリック メソッドまたはプロテクト メソッドが System.Runtime.InteropServices.DllImportAttribute 属性を使用してマークされています。  アンマネージ ライブラリの位置を特定できないか、メソッドがライブラリ内の関数と一致しません。|  
|[CA1401: P\/Invoke は参照可能になりません](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)|パブリック型のパブリック メソッドまたはプロテクト メソッドに、System.Runtime.InteropServices.DllImportAttribute 属性があります \(Visual Basic では Declare キーワードでも実装されます\)。  このようなメソッドは公開しないでください。|  
|[CA1402: COM 参照可能インターフェイスでのオーバーロードを避けてください](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|オーバーロードされたメソッドが COM クライアントに公開されると、最初のメソッド オーバーロードだけが名前を保持します。  後続のオーバーロードは、名前にアンダースコア文字 \(\_\) およびオーバーロードの宣言の順序に対応する整数が付加され、一意の名前に変更されます。|  
|[CA1403: Auto 配置の型を COM 参照可能にすることはできません](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|COM 参照可能な値型が、LayoutKind.Auto に設定された System.Runtime.InteropServices.StructLayoutAttribute 属性を使用してマークされています。  これらの型のレイアウトは [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンによって異なる場合があるため、特定のレイアウトを必要とする COM クライアントが動作しなくなる可能性があります。|  
|[CA1404: P\/Invoke の直後に GetLastError を呼び出します](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Marshal.GetLastWin32Error メソッドまたは同等の [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError 関数が呼び出されました。その直前に、プラットフォーム呼び出しメソッドが呼び出されていません。|  
|[CA1405: COM 参照可能な型の基本型は COM 参照可能でなければなりません](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 参照可能な型が、COM 参照不可能な型から派生しています。|  
|[CA1406: Visual Basic 6 クライアントに対しては Int64 引数を使用しません](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Visual Basic 6 COM クライアントでは、64 ビット整数にアクセスできません。|  
|[CA1407: Com 参照可能な型で静的メンバーを使用しません](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)|COM では静的メソッドをサポートしていません。|  
|[CA1408: AutoDual ClassInterfaceType を使用しないでください](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|デュアル インターフェイスを使用する型を使用することで、クライアントを特定のインターフェイス レイアウトに対応付けることができます。  将来のバージョンで、この型またはその基本型のレイアウトに変更が加えられると、インターフェイスに対応付けられた COM クライアントが切り離されます。  既定では、ClassInterfaceAttribute 属性が指定されていない場合、ディスパッチ専用インターフェイスが使用されます。|  
|[CA1409: COM 参照可能な型は作成可能でなければなりません](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|COM から参照できると明確にマークされている参照型に、パブリックのパラメーター付きコンストラクターが含まれますが、パブリックの既定 \(パラメーターなし\) コンストラクターが含まれません。  パブリックの既定コンストラクターがない型は、COM クライアントで作成できません。|  
|[CA1410: COM 登録メソッドは一致しなければなりません](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 属性を使用してマークされたメソッドが型で宣言されているが、<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 属性を使用してマークされたメソッドが宣言されていません。または、その逆の状態になっています。|  
|[CA1411: COM 登録メソッドは参照可能であることはできません](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|System.Runtime.InteropServices.ComRegisterFunctionAttribute 属性または System.Runtime.InteropServices.ComUnregisterFunctionAttribute 属性を使用してマークされたメソッドが外部から参照できます。|  
|[CA1412: ComSource インターフェイスを IDispatch として設定します](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|型が System.Runtime.InteropServices.ComSourceInterfacesAttribute 属性によってマークされていますが、1 つ以上の指定されたインターフェイスが ComInterfaceType.InterfaceIsIDispatch に設定された System.Runtime.InteropServices.InterfaceTypeAttribute 属性によってマークされていません。|  
|[CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|COM から参照できる値型の非パブリック インスタンス フィールドは、COM クライアントで表示できます。  フィールドの内容を調べて、公開するべきではない情報や、設計またはセキュリティに意図しない影響を及ぼす情報が含まれていないかどうかを確認してください。|  
|[CA1414: ブール型の P\/Invoke 引数を MarshalAs に設定します](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Boolean データ型は、アンマネージ コードの複数の表現を持っています。|  
|[CA1415: P\/Invoke を正しく宣言します](../code-quality/ca1415-declare-p-invokes-correctly.md)|この規則では、OVERLAPPED 構造体パラメーターへのポインターを持ち、対応するマネージ型パラメーターが <xref:System.Threading.NativeOverlapped?displayProperty=fullName> 構造体へのポインターではない [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] 関数に対するプラットフォーム呼び出しメソッド宣言が対象になります。|