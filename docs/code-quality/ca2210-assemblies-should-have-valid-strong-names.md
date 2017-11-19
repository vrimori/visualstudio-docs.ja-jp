---
title: "Ca 2210: アセンブリは有効な厳密な名前である必要があります |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 11e50cb87364a85d0c97ae5e566b1209696febbd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: アセンブリには有効な厳密な名前が必要です
|||  
|-|-|  
|TypeName|AssembliesShouldHaveValidStrongNames|  
|CheckId|CA2210|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 アセンブリが厳密な名前で署名されていない、厳密な名前を検証できませんでした、または厳密な名前をコンピューターの現在のレジストリ設定なしでも有効にすることはできません。  
  
## <a name="rule-description"></a>規則の説明  
 このルールは、取得し、アセンブリの厳密な名前を確認します。 違反は、次のいずれかに当てはまる場合に発生します。  
  
-   アセンブリの厳密な名前ではありません。  
  
-   アセンブリが署名後に変更されました。  
  
-   アセンブリに遅延署名します。  
  
-   アセンブリが正しく署名されていない、または署名できませんでした。  
  
-   アセンブリには、レジストリ設定の検証に合格する必要があります。 たとえば、アセンブリの検証をスキップする、厳密名ツール (Sn.exe) が使用されました。  
  
 厳密な名前によって、改ざんされたアセンブリを、クライアントが無意識のうちに読み込む問題を防ぐことができます。 厳密な名前のないアセンブリが配置される状況は、限定されます。 適切に署名されていないアセンブリを共有または配布すると、アセンブリが改ざんされる場合、共通言語ランタイムでアセンブリを読み込むことができない場合、またはユーザーのコンピューターで検証を無効にする必要がある場合などの問題が考えられます。 厳密な名前のないアセンブリでは、次の欠点があります。  
  
-   その元のドメインを確認できません。  
  
-   共通言語ランタイムは、アセンブリの内容が変更されたかどうかをユーザーに警告ことはできません。  
  
-   グローバル アセンブリ キャッシュに読み込むことができません。  
  
 読み込むことに注意し、遅延署名アセンブリを分析、アセンブリの検証を無効にする必要があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 **キー ファイルを作成するには**  
  
 次の手順のいずれかを使用します。  
  
-   によって提供されるアセンブリ リンカー ツール (Al.exe) を使用して、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK。  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] V1.0 または v1.1 を使用するか、<xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>または<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>属性。  
  
-   [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]、いずれかを使用して、`/keyfile`または`/keycontainer`コンパイラ オプション[/KEYFILE (を指定するキーまたはキー ペア アセンブリに署名する)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly)または[/KEYCONTAINER (アセンブリに署名するキー コンテナーを指定してください)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) c++ リンカー オプション)。  
  
 **Visual Studio での厳密な名前でアセンブリに署名するには**  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューションを開きます。  
  
2.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティです。**  
  
3.  クリックして、**署名**タブをクリックし、選択、**アセンブリに署名**チェック ボックスをオンします。  
  
4.  **厳密な名前キー ファイルを選択して****新規**です。  
  
     **厳密な名前キーの作成**ウィンドウに表示されます。  
  
5.  **キー ファイル名**、厳密な名前キーの名前を入力します。  
  
6.  パスワードでキーを保護し、をクリックするかどうかを選択して**OK**です。  
  
7.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**ビルド**です。  
  
 **Visual Studio の外部の厳密な名前でアセンブリに署名するには**  
  
-   提供されている厳密名ツール (Sn.exe) を使用して、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK。 詳細については、「[Sn.exe (厳密名ツール)](/dotnet/framework/tools/sn-exe-strong-name-tool)」を参照してください。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 アセンブリが環境で使用されている場合のみこの規則による警告は抑制改ざんが問題にならない場合です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>   
 <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>   
 [方法 : 厳密な名前でアセンブリに署名する](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)   
 [Sn.exe (厳密名ツール)](/dotnet/framework/tools/sn-exe-strong-name-tool)