---
title: "VSIX v3 で Ngen のサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 46b6f4d13b4c1938797dbe6cf6023e3c8c42d1ed
ms.lasthandoff: 03/07/2017

---
# <a name="ngen-support-in-vsix-v3"></a>VSIX v3 で Ngen のサポート

Visual Studio 2017 と新しい VSIX v3 (バージョン 3) 拡張機能マニフェスト形式、拡張機能の開発者できるようになりました"ngen"のインストール時のアセンブリ。

どのような"ngen"について説明します MSDN からの抜粋を次に示します。

>ネイティブ イメージ ジェネレーター (Ngen.exe) は、マネージ アプリケーションのパフォーマンスを向上するツールです。 Ngen.exe は、コンパイルされたプロセッサ固有のマシン コードを含むファイルであるネイティブ イメージを作成してローカル コンピューターのネイティブ イメージ キャッシュにインストールします。 ランタイムは、Just-In-Time (JIT) コンパイラを使用してオリジナルのアセンブリをコンパイルする代わりに、キャッシュにあるネイティブ イメージを使用できます。
>
>[Ngen.exe (ネイティブ イメージ ジェネレーター)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

アセンブリが"ngen"で、VSIX を「インスタンスごとのコンピューターごとの」インストールする必要があります。 これは、extension.vsixmanifest の各デザイナーで"all users"チェック ボックスをオンに有効にすることができます。

![すべてのユーザーを確認します。](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Ngen を有効にする方法

使用できるアセンブリを ngen を有効にする、**プロパティ**Visual Studio のウィンドウです。

設定できる 4 つのプロパティがあります。

1. **Ngen** (Boolean)-true の場合、Visual Studio インストーラーは"ngen"アセンブリ。
2. **Ngen アプリケーション**(文字列) – Ngen はアセンブリの依存関係を解決するために、アプリケーションの app.config ファイルを使用する機会を提供します。 この値は、アプリケーションの app.config を使用 (Visual Studio インストール ディレクトリ) を基準とする場合に設定する必要があります。
3. **Ngen アーキテクチャ**(列挙) – アーキテクチャが、アセンブリをネイティブにコンパイルします。 オプションは、: します。 NotSpecified b とします。 X86 c です。 X64 d です。 すべて
4. **Ngen の優先順位**(1 から 3 までの整数) –、Ngen の優先度レベルの詳細については、 [Ngen.exe の優先順位レベル](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3)します。

この記事では、**プロパティ**ウィンドウの動作。

![プロパティで ngen](media/ngen-in-properties.png)

これにより、プロジェクト参照を VSIX プロジェクトの .csproj ファイル内にメタデータが追加されます。

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
 ```

 >**注:**したい場合、.csproj ファイルを直接、編集することができます。

## <a name="extra-information"></a>追加情報

プロパティのデザイナー変更はプロジェクト参照だけに適用します。同様に、プロジェクト内で項目の Ngen メタデータを設定することができます (を使用して上記の同じ方法)、項目は、.NET アセンブリ限りです。
