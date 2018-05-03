---
title: クラス デザイナーの Visual C++ 構造体
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 36d9e78a1944817d9384d0c55b9584e58a758ccc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="visual-c-structures-in-class-designer"></a>クラス デザイナーの Visual C++ 構造体

**クラス デザイナー**は、C++ の構造体をサポートしています。これは、`struct` キーワードを使用して宣言されます。 例を次に示します。

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

`struct` 型の使用法の詳細については、「[struct](/cpp/cpp/struct-cpp)」を参照してください。

クラス ダイアグラムにおける C++ 構造体の図形の形状と動作はクラスの図形に似ていますが、ラベルが **[Struct]** である点と、角が丸くなく直角である点が異なります。

|コード要素|クラス デザイナー ビュー|
|------------------|-------------------------|
|`struct StructureName {};`|**StructureName**<br /><br /> 構造体|

## <a name="see-also"></a>関連項目

- [Visual C++ コードの使用](working-with-visual-cpp-code.md)
- [クラスと構造体](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)