---
title: "VSIX v3 で Ngen サポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 15277f0a1038e43bb316d604cbc415da4a5d80bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ngen-support-in-vsix-v3"></a>VSIX v3 の Ngen のサポート

Visual Studio 2017 と新しい VSIX v3 (バージョン 3) の拡張機能マニフェスト形式、拡張機能の開発者できるようになりました"ngen"、アセンブリのインストール時にします。

次にどのような"ngen"はについて説明します。 MSDN からの抜粋を示します。

>ネイティブ イメージ ジェネレーター (Ngen.exe) は、マネージ アプリケーションのパフォーマンスを向上するツールです。 Ngen.exe は、コンパイルされたプロセッサ固有のマシン コードを含むファイルであるネイティブ イメージを作成してローカル コンピューターのネイティブ イメージ キャッシュにインストールします。 ランタイムは、Just-In-Time (JIT) コンパイラを使用してオリジナルのアセンブリをコンパイルする代わりに、キャッシュにあるネイティブ イメージを使用できます。
>
>[Ngen.exe (ネイティブ イメージ ジェネレーター)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

アセンブリが"ngen"するには、VSIX を「インスタンスごとのコンピューターごとの」インストールする必要があります。 これは、extension.vsixmanifest の各デザイナーで"all users"チェック ボックスをオンに有効にすることができます。

![すべてのユーザーを確認します。](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Ngen を有効にする方法

アセンブリを ngen を有効にするのに使用することができます、**プロパティ**Visual Studio のウィンドウ。

設定できる 4 つのプロパティがあります。

1. **Ngen** (ブール値) の場合は true、Visual Studio インストーラーは"ngen"アセンブリ。
2. **Ngen アプリケーション**(string) - Ngen は、アセンブリの依存関係を解決するために、アプリケーションの app.config ファイルを使用する機会を提供します。 アプリケーションの app.config に (Visual Studio インストール ディレクトリ) への相対使用するのには、この値を設定する必要があります。
3. **Ngen アーキテクチャ**(列挙) のアーキテクチャが、アセンブリをネイティブにコンパイルします。 オプションは、: します。 NotSpecified b とします。 X86 c です。 D X64。 すべて
4. **Ngen の優先度**(1 ~ 3 の範囲の整数) で、Ngen の優先度レベルについては、 [Ngen.exe 優先度レベル](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3)です。

ここを見て、**プロパティ**アクション ウィンドウ。

![プロパティで ngen](media/ngen-in-properties.png)

これにより、VSIX プロジェクトの .csproj ファイル内でプロジェクト参照にメタデータが追加されます。

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

プロジェクト参照単にプロパティ デザイナー変更が適用します。プロジェクト内でアイテムの Ngen メタデータを設定することができます (を使用して上記の同じ方法)、項目は、.NET アセンブリ限りです。