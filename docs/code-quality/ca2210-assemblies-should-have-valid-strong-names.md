---
title: 'CA2210: アセンブリには有効な厳密な名前が必要です'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd22b0e28859ea153466b58f5f27ab458f5aa529
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858945"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: アセンブリには有効な厳密な名前が必要です

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

アセンブリが厳密な名前で署名されていないと、厳密な名前を確認できませんでした、または、厳密な名前をコンピューターの現在のレジストリ設定なしでも有効にすることはできません。

## <a name="rule-description"></a>規則の説明

このルールを取得し、アセンブリの厳密な名前を確認します。 違反は、次のいずれかに当てはまる場合に発生します。

- アセンブリの厳密な名前ではありません。

- アセンブリが署名後に変更されました。

- アセンブリは、遅延署名します。

- アセンブリが正しく署名されていない、または署名に失敗しました。

- アセンブリには、レジストリ設定の検証に合格する必要があります。 たとえば、アセンブリの検証をスキップする厳密な名前ツール (Sn.exe) が使用されました。

厳密な名前によって、改ざんされたアセンブリを、クライアントが無意識のうちに読み込む問題を防ぐことができます。 厳密な名前のないアセンブリが配置される状況は、限定されます。 適切に署名されていないアセンブリを共有または配布すると、アセンブリが改ざんされる場合、共通言語ランタイムでアセンブリを読み込むことができない場合、またはユーザーのコンピューターで検証を無効にする必要がある場合などの問題が考えられます。 厳密な名前のないアセンブリを持つ次の欠点があります。

- その生成元を検証できません。

- 共通言語ランタイム アセンブリの内容が変更されたかどうかのユーザーに警告ことはできません。

- それは、グローバル アセンブリ キャッシュに読み込むことができません。

読み込みおよび、遅延署名アセンブリを分析するアセンブリの検証を無効する必要がありますに注意してください。

## <a name="how-to-fix-violations"></a>違反の修正方法

### <a name="create-a-key-file"></a>キー ファイルを作成します。

次の手順のいずれかを使用します。

- .NET Framework SDK によって提供される、アセンブリ リンカー ツール (Al.exe) を使用します。

- .NET Framework v1.0 または v1.1 では、いずれかの操作を使用して、<xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>または<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>属性。

- [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]、いずれかを使用して、`/keyfile`または`/keycontainer`コンパイラ オプション[/KEYFILE (指定のキーまたはキー ペア アセンブリに署名する)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly)または[/KEYCONTAINER (アセンブリに署名するキー コンテナーの指定)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) C++ でリンカー オプション)。

### <a name="sign-your-assembly-with-a-strong-name-in-visual-studio"></a>Visual Studio での厳密な名前でアセンブリに署名します。

1. Visual Studio でソリューションを開きます。

2. **ソリューション エクスプ ローラー**プロジェクトを右クリックし、クリックして**プロパティ。**

3. をクリックして、**署名**タブをクリックし、選択、**アセンブリに署名**チェック ボックスをオンします。

4. **厳密な名前キー ファイルを選択して**、**新規**します。

   **厳密な名前キーの作成**ウィンドウに表示されます。

5. **キー ファイル名**、厳密な名前キーの名前を入力します。

6. クリックして、パスワードでキーを保護するかどうかを選択して**OK**します。

7. **ソリューション エクスプ ローラー**プロジェクトを右クリックし、クリックして**ビルド**します。

### <a name="sign-your-assembly-with-a-strong-name-outside-visual-studio"></a>Visual Studio の外部の厳密な名前でアセンブリに署名します。

.NET Framework SDK によって提供される厳密な名前ツール (Sn.exe) を使用します。 詳細については、「[Sn.exe (厳密名ツール)](/dotnet/framework/tools/sn-exe-strong-name-tool)」を参照してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

アセンブリは、環境で使用する場合のみこの規則による警告を抑制する内容の改ざんが問題にならない場合。

## <a name="see-also"></a>関連項目

- <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>
- <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
- [方法: 厳密な名前でアセンブリに署名する](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Sn.exe (厳密名ツール)](/dotnet/framework/tools/sn-exe-strong-name-tool)