---
title: "アプリケーション リソースの管理 (.NET) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 5cb2e044f5c55881adade6d3022fc453360a2e9c
ms.contentlocale: ja-jp
ms.lasthandoff: 05/30/2017

---
# <a name="managing-application-resources-net"></a>アプリケーション リソースの管理 (.NET)
リソース ファイルとは、アプリケーションの一部ですが、コンパイルされないファイルのことであり、たとえばアイコン ファイルやオーディオ ファイルが該当します。 これらのファイルはコンパイル処理の一部ではないため、バイナリを再コンパイルする必要なしで変更することができます。 アプリケーションをローカライズすることを計画している場合は、アプリケーションをローカライズするときに変更する必要があるすべての文字列とその他のリソースに関して、リソース ファイルを使用する必要があります。  
  
 .NET デスクトップ アプリ内のリソースの詳細については、「[デスクトップ アプリケーションのリソース](/dotnet/framework/resources/index)」を参照してください。 C++ デスクトップ アプリ内でのリソースの詳細については、「 [Working with Resource Files](/cpp/windows/working-with-resource-files)」を参照してください。  
  
 Windows ストア アプリは、デスクトップ アプリとは異なる別のリソース モデルを使用します。 Windows ストア アプリ内のリソースの詳細については、Windows デベロッパー センター Web サイトの「 [アプリケーション リソースの定義](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx) 」を参照してください。  
  
## <a name="working-with-resources"></a>リソースの操作  
 マネージ コード プロジェクト内で、プロジェクトのプロパティ ウィンドウを開くために、 **ソリューション エクスプローラー** でプロジェクト ノードを右クリックして **[プロパティ]**をクリックするか、 **[クイック起動]** ウィンドウに **プロジェクトのプロパティ** を入力するか、 **ソリューション エクスプローラー** ウィンドウ内で Alt キーを押しながら Enter キーを押します。 **[リソース]** タブをクリックします。 プロジェクトにまだ .resx ファイルが含まれていない場合や、異なる種類のリソースを追加および削除する場合、また既存のリソースを変更する場合は、.resx ファイルを追加できます。  
  
 C++ プロジェクトでのリソースの操作方法については、「[方法: リソースを作成する](/cpp/windows/how-to-create-a-resource)」を参照してください。
