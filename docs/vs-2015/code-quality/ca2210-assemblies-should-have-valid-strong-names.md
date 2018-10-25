---
title: 'Ca 2210: アセンブリが有効な厳密な名前 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1551cccb11fc33a21503e7030cfd671c953ee17d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865818"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: アセンブリには有効な厳密な名前が必要です
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 **キー ファイルを作成するには**

 次の手順のいずれかを使用します。

- によって提供されるアセンブリ リンカー ツール (Al.exe) を使用して、 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK。

- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] V1.0 または v1.1 を使用するか、<xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>または<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>属性。

- [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]、いずれかを使用して、`/keyfile`または`/keycontainer`コンパイラ オプション[/KEYFILE (指定のキーまたはキー ペア アセンブリに署名する)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06)または[/KEYCONTAINER (アセンブリに署名するキー コンテナーの指定)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) C++ でリンカー オプション)。

  **Visual Studio での厳密な名前でアセンブリに署名するには**

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ソリューションを開きます。

2. **ソリューション エクスプ ローラー**プロジェクトを右クリックし、クリックして**プロパティ。**

3. をクリックして、**署名**タブをクリックし、選択、**アセンブリに署名**チェック ボックスをオンします。

4. **厳密な名前キー ファイルを選択して**、**新規**します。

    **厳密な名前キーの作成**ウィンドウに表示されます。

5. **キー ファイル名**、厳密な名前キーの名前を入力します。

6. クリックして、パスワードでキーを保護するかどうかを選択して**OK**します。

7. **ソリューション エクスプ ローラー**プロジェクトを右クリックし、クリックして**ビルド**します。

   **Visual Studio の外部の厳密な名前でアセンブリに署名するには**

-   によって提供される厳密な名前ツール (Sn.exe) を使用して、 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK。 詳細については、「[Sn.exe (厳密名ツール)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)」を参照してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 アセンブリは、環境で使用する場合のみこの規則による警告を抑制する内容の改ざんが問題にならない場合。

## <a name="see-also"></a>関連項目
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [方法: 厳密な名前でアセンブリに署名](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (厳密名ツール)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)



