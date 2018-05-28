---
title: JavaScript
description: Visual Studio for Mac の JavaScript サポートに関する情報
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: b24591053162603ed3089c0868d215a101688f7e
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="javascript-support"></a>JavaScript サポート

Visual Studio for Mac では、構文の強調表示、コードの書式設定、IntelliSense で JavaScript と TypeScript を利用できます。 

![TypeScript エディター サポート](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

JavaScript のコード記述に関する詳細については、「[JavaScript コードの記述](https://docs.microsoft.com/scripting/javascript/writing-javascript-code)」ガイドを参照してください。

## <a name="adding-a-javascript-file"></a>JavaScript ファイルの追加

JavaScript ファイルはほとんどの場合、**[新しいファイル]** ダイアログから ASP.NET Core プロジェクトに追加されます。 JavaScript ファイルを追加するには、プロジェクトを右クリックし、**[追加]、[新しいファイル]** の順に進みます。 

![プロジェクトに新しいファイルを追加する](media/javascript-image1.png)

[新しいファイル] ダイアログから、**[Web]、[Empty JS file]\(空の JS ファイル\)** の順に選択するか、**[Web]、[TypeScript ファイル]** の順に選択します。 名前を付けて **[新規]** を選択します。

![テンプレートから新しい TypeScript ファイルを作成する](media/javascript-image2.png)

## <a name="intellisense"></a>Intellisense

Visual Studio for Mac は [JavaScript 言語サービス](https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense)を使用して Intellisense を提供します。コード記述において、インテリジェントなコード補完、パラメーター情報、メンバー リストが与えられます。

Visual Studio for Mac の JavaScript IntelliSense は、型の推定、JSDoc、または TypeScript 宣言を基盤にすることができます。

- **型の推定** - コードの前後関係からオブジェクトの型を割り出します。 詳細については、「[型推論に基づく IntelliSense](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference)」の Visual Studio セクションを参照してください。
- **JSDoc** - 型の推定では正しい型情報が与えられないことがあります。 そのような場合、型情報は [JSDoc](http://usejsdoc.org/about-getting-started.html) 注釈によって明示的に指定できます。 詳細については、「[JSDoc に基づく IntelliSense](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)」の Visual Studio セクションを参照してください。
- **TypeScript 宣言ファイル** - `.d.ts` ファイルを利用し、JavaScript IntelliSense の値が与えられます。 そのファイルに宣言されている型を JSDoc コメントで型として使用できます。 詳細については、「[TypeScript 宣言ファイルに基づく IntelliSense](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files)」の Visual Studio セクションを参照してください。 ![TypeScript 定義ファイルの追加](media/javascript-image3.png)