---
title: VSIX v3 で Ngen のサポート |Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b316efe4abc9f14608db2e61602ac882c7208234
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958694"
---
# <a name="ngen-support-in-vsix-v3"></a>VSIX v3 での Ngen のサポート

Visual Studio 2017 と、新しい VSIX v3 (バージョン 3) の拡張機能マニフェスト形式、拡張機能の開発者できるようになりました"ngen"のインストール時にそのアセンブリ。

どのような"ngen"がについて説明します。 MSDN からの抜粋を次に示します。

>ネイティブ イメージ ジェネレーター (*Ngen.exe*) は、マネージ アプリケーションのパフォーマンスを向上させるツールです。 *Ngen.exe* 、コンパイルされたプロセッサ固有のマシン コードを含むファイルは、ローカル コンピューターのネイティブ イメージ キャッシュにインストールするネイティブ イメージを作成します。 ランタイムは、Just-In-Time (JIT) コンパイラを使用してオリジナルのアセンブリをコンパイルする代わりに、キャッシュにあるネイティブ イメージを使用できます。
>
>[Ngen.exe (ネイティブ イメージ ジェネレーター)](/dotnet/framework/tools/ngen-exe-native-image-generator)

アセンブリが"ngen"で、VSIX を「インスタンス単位、コンピューターごと」インストールする必要があります。 これは、「すべてのユーザー」のチェック ボックスを確認して有効にできます、`extension.vsixmanifest`デザイナー。

![すべてのユーザーを確認してください。](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Ngen を有効にする方法

アセンブリで ngen を有効にするを使用できます、**プロパティ**Visual Studio のウィンドウ。

設定できる 4 つのプロパティがあります。

1. **Ngen** (Boolean) - true の場合、Visual Studio インストーラーでの"ngen"アセンブリ。
2. **Ngen アプリケーション**(文字列) - アプリケーションを使用する機会を提供する Ngen *app.config*アセンブリの依存関係を解決するためにファイル。 この値に設定するアプリケーションが*app.config* (Visual Studio インストール ディレクトリ) を基準に使用します。
3. **Ngen アーキテクチャ**(列挙) のアーキテクチャをアセンブリをネイティブにコンパイルします。 オプションを: します。 B の notspecified です。 X86 c。 X64 d。 すべて
4. **Ngen の優先度**(1 ~ 3 の範囲の整数) で、Ngen の優先度レベルについては、 [Ngen.exe の優先度レベル](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)します。

ここを参照してください、**プロパティ**ウィンドウの動作。

![ngen のプロパティ](media/ngen-in-properties.png)

これは、メタデータが、VSIX プロジェクトの内部でプロジェクト参照に追加されます *.csproj*ファイル。

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

 >**注:** たい場合は、.csproj ファイルを直接編集できます。

## <a name="extra-information"></a>追加情報

プロパティのデザイナーの変更; プロジェクトの参照だけに適用されます。プロジェクト内で項目の Ngen のメタデータを設定することができます (を使用して上記で説明したのと同じ方法) 長く、項目は .NET アセンブリです。